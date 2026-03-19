---
license: cc-by-4.0
tags:
- education
- dialogue
- chats
pretty_name: study_chats
size_categories:
- 10K<n<100K
language:
- en
configs:
- config_name: combined
  data_files: "data.jsonl"
---

# The StudyChat Dataset: Student Dialogues With ChatGPT in an Artificial Intelligence Course

## Updates

**v1.0 - Summer 2025 Update**
- New Dialogues from Spring 2025 Semester 
- Greatly Improved Dialogue Act Labeling using `GPT4.1`
- Assignment Details Added for Both Semesters
- Scores of Consented Students Added
- Included 900+ Assignment Submissions

**v0.1 – Initial Release**
- Initial chats from the Fall 2024 semester uploaded
- PII and toxicity filtered
- Includes LLM-generated dialogue act labels
- Added license and README

## Description

This dataset contains real-world student interactions with a large language model (LLM)-based virtual assistant, collected during an undergraduate artificial intelligence course, COMPSCI 383, at the University of Massachusetts Amherst in the Fall 2024 - Spring 2025 calendar year.

The assistant was deployed to help students with open-ended programming questions across several course assignments and was designed to mirror ChatGPT functionality.

Initial findings and many more details on this dataset can be found at the following paper, ["The StudyChat Dataset: Student Dialogues With ChatGPT in an Artificial Intelligence Course"](https://arxiv.org/abs/2503.07928), which outlines the process by which this dataset was formed and investigates student dialogue behavior and it's correlations with learning outcomes.

## Dataset Contents

The dialogues are provided in a single `.jsonl` file containing a list of dialog sessions. Additional context, grades, and further information can be found in the `v1` directory.

Each dialogue entry includes:
- `prompt`: The final user message before the assistant’s response
- `response`: The final assistant message in the conversation
- `topic`: Assignment or topic identifier (e.g., `a1` through `a7`)
- `messages`: The full message history of the interaction (user/system/assistant turns)
- `timestamp`: Unix timestamp of when the user prompt was sent to the assistant
- `chatStartTime`: Timestamp marking the first user request in the conversation
- `chatId`: Unique identifier for the conversation
- `userId`: An anonymized user identifier
- `interactionCount`: Number indicating the turn index in the broader conversation
- `chatTotalInteractionCount`: Number indicating the total turns for the given `chatId`
- `llm_label`: A label generated via prompting `GPT-4.1` to indicate the dialogue act or intent of the student message
- `semester`: A label indicating which semester during which the conversation occurred ("f24" or "s25")

**Example:**

```json
{
  "prompt": "how to build a tree given a txt",
  "response": "Building a tree (data structure) from a text file can be accomplished in various ways...",
  "topic": "a2",
  "messages": [
    {
      "role": "system",
      "content": "You are a helpful assistant."
    },
    {
      "role": "user",
      "content": "how to build a tree given a txt"
    }
  ],
  "timestamp": 1740201613871,
  "chatId": "d8606067-2553-42ea-974a-d5fe42cd0e0a",
  "userId": "919be590-7081-7003-3cef-906e621826ff",
  "interactionCount": 0,
  "chatTitle": "how to build",
  "chatStartTime": "2025-02-22T00:20:01.277385",
  "chatTotalInteractionCount": 17,
  "llm_label": {
    "label": "conceptual_questions>Computer Science",
    "justification": "The user is asking a conceptual question about how to construct a tree data structure from a text file, which is a core computer science concept relevant to the assignment."
  },
  "semester": "f24"
}
```

## Dataset Creation and Cleaning

- Collected from a deployed LLM assistant (ChatGPT-based) used in a university course setting.
- Participants opted in to have their conversations included in the dataset.
- All user identifiers are anonymized.
- Personally identifiable information (PII) was filtered using an iterative regex-based pipeline.
- Potentially harmful content was analyzed and filtered using OpenAI's Moderation API.
- Each conversation was labeled with a hierarchical dialogue act schema via LLM prompting.

## Considerations & Limitations

- This dataset is drawn from a specific course context and may not generalize to other educational settings.
- LLM-generated labels may contain noise or uncertainty.
- The assistant responses reflect the behavior of specific LLM `gpt4o-mini` the free tier of ChatGPT at the time of the study
- Intended for research or educational purposes only.

## License

This dataset is licensed under a [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).  

If you use the exercises in a classroom setting, please attribute the authors appropriately.

If you use this dataset in your work, please cite the dataset as:

```bibtex
@misc{mcnichols2025studychatdatasetstudentdialogues,
      title={The StudyChat Dataset: Student Dialogues With ChatGPT in an Artificial Intelligence Course}, 
      author={Hunter McNichols and Fareya Ikram and Andrew Lan},
      year={2025},
      eprint={2503.07928},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2503.07928}, 
}
```

## Contact & Feedback

- [Start a Discussion on HuggingFace](https://huggingface.co/datasets/wmcnicho/StudyChat/discussions)  
- Email: wmcnichols@umass.edu