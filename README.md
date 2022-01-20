# Health Coaching Dialogue Corpus

Health coaching has been recognized as a successful approach for encouraging health behavior changes by having a professional provide evidence-based interventions, setting realistic goals, and encouraging goal adherence. However, health coaching is expensive, time-intensive, and unavailable around the clock.  Therefore, we aim to build a health coaching dialogue system that converses with the patients via text messages and helps them to set Specific, Measurable, Attainable, Realistic, and Time-bound (S.M.A.R.T.) goals.

We conducted two rounds of data collection, where we recruited patients who  exchanged SMS  with certified health coaches for several weeks. Each week the coach conversed with the patients to set, follow up, and evaluate S.M.A.R.T. goals.  We share the data from the second round, as allowed by the IRB approval (protocol 2016-0862, University of Illinois at Chicago), for those  patients who explicitly  consented to the release. The dataset is thoroughly de-identified. We regret that we cannot release the data from the first round of data collection.

This corpus has been referenced in the following papers:

*  **[Human-Human Health Coaching via Text Messages: Corpus, Annotation, and Analysis](https://aclanthology.org/2020.sigdial-1.30/ )**. SIGDIAL 2020.
*  **[Goal Summarization for Human-Human Health Coaching Dialogues](https://www.aaai.org/ocs/index.php/FLAIRS/FLAIRS20/paper/view/18455/17608)**. FLAIRS 2020.
*  **[Summarizing Behavioral Change Goals from SMS Exchanges to Support Health Coaches](https://aclanthology.org/2021.sigdial-1.31/)**. SIGDIAL 2021.

## Dataset

In the second round, we recruited 30 patients who participated in the study for eight weeks; they are numbered from 01 to 30. The release contains data for 26 patients, because four patients (ids: 01, 02, 10, and 15)  did not consent to the release of their data. We include the data in its entirety, other than messages at the end of the study, that pertain to the logistics of an in-person exit interview. Additionally, two patients' data (id: 6 and id: 13) contains much less information since they did not complete the study. Please note that the models  in our papers were evaluated on data from 28 patients from round two, since we did exclude patients 6 and 13, and used all the rest of the data.

This repository contains two files:

```
|--/human_labeled
| |--patient5_smart.xml
| |--patient5_phases.xml
| |--patient7_smart.xml
| |--patient7_phases.xml
```
The `human_labeled` file contains the dialogue metatext for patient #5 and #7 with SMART tags and goal phases labeled manually (ground truth) using GATE. The stage labels (i.e., the stage for each week, which is either goal\_setting or goal\_action) are also included in the *phases.xml files.

```
|--/raw_with_predict_labels
| |--patient3.csv
| |--patient4.csv
| |--patient5.csv
| |--    ...
```

The `raw_with_predict_labels` file contains all the raw dialogue texts for the patient from #3 to #30, excluding #10, and #15, with the model-predicted SMART tags, phases, and dialogue act labels for potential user references. The columns are:

* *id*: unique ID of the utterances in the order of conversation sequence.
* *speaker*: the interlocutor of the utterance, which is either *coach* or *patient*.
* *utterance*: the de-identified content of the utterances.
* *time*: the time stamp of the utterance.
* *smart*: the *predicted* sequential labels of the SMART tags for each token of an utterance. 'O' indicates that the corresponding token has no SMART tag. See a detailed explanation below.
* *tokens*: the tokenized utterance, a list of tokens used for smart attribute and phase prediction.
* *phases*: the *predicted* goal phases indicated by the content of utterance. For example, "Great job on your steps yesterday you walked over 2,500! Keep it up today!" is predicted as a follow-up phase.  
* *act*: the *predicted* dialogue act based on the content of utterance.
* *stage*: indicates the stage for each week, which is either goal\_setting or goal\_action. The goal\_setting stage also indicates the beginning of each week. Note this column is *manually* labeled.


For the SMART tags used and corresponding abbreviation/examples:
* *SA*:'specificity-activity', activity, e.g., walk, jog,
* *ST*:'specificity-time', time, e.g., between 6 and 8, during lunch time,
* *SL*:'specificity-location', location, e.g., 'at work', 'in the house'
* *MQAmt*: 'measurability-number', amount, e.g., '7700 steps', '5 flights'
* *MQDist*: 'measurability-distance', distance, e.g., 2 miles, 3 blocks, from bus stop to walmart
* *MQDur*: 'measurability-duration',#duration, e.g., 40min
* *MDName*: 'measurability-name', day names e.g., fri, monday, mon wed
* *MDNum*: 'measurability-other', day numbers, 5 days, every day
* *MRep*:'measurability-repetition', repetition e.g., twice a day, once a day, daily
* *AS*:'attainability-score', attainability, e.g., 10, 9, 8

For details regarding how these labels are defined and predicted please refer to the papers listed above.

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
## Citation
```bibtex
@inproceedings{gupta-etal-2020-human,
    title = "Human-Human Health Coaching via Text Messages: Corpus, Annotation, and Analysis",
    author = "Gupta, Itika  and
      Di Eugenio, Barbara  and
      Ziebart, Brian  and
      Baiju, Aiswarya  and
      Liu, Bing  and
      Gerber, Ben  and
      Sharp, Lisa  and
      Nabulsi, Nadia  and
      Smart, Mary",
    booktitle = "Proceedings of the 21th Annual Meeting of the Special Interest Group on Discourse and Dialogue",
    month = jul,
    year = "2020",
    address = "1st virtual meeting",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2020.sigdial-1.30",
    pages = "246--256",
}
```
## Acknowledgment

This data was collected under award [# 1838770 SCH: INT: The Virtual Assistant Health Coach: Learning to Autonomously Improve Health Behaviors](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1838770), by the US National Science Foundation.
