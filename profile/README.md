# BM5201 – Data Mining · Course Project

**Course organization:** [github.com/bm5201-2026](https://github.com/bm5201-2026)

Welcome! In this project you (individually or as a group) take part in an **international shared task / challenge**
(SemEval-2027, ICASSP 2027 Grand Challenges, …) and document the full data-mining workflow
on GitHub. All project repositories live in this organization, where they are followed
and evaluated. Each student or group can see **only their own repository**.

---

## 1. Approved challenges

| Challenge | Link |
|-----------|------|
| SemEval-2027 Task 12 – ArtEmotion-28 | official task page |
| SemEval-2027 Task 9 – Analysis of Multimodal Framing in the News | [propaganda.math.unipd.it/semeval2027task9](https://propaganda.math.unipd.it/semeval2027task9/) |
| SemEval-2027 – RETECO | official task page |
| RMS-AQA – Real-world Multi-hop Spatial Audio Question Answering | official task page |
| ICASSP 2027 – 2nd X-to-Audio Alignment Challenge (XACLE) | [xacle.org/2027](https://xacle.org/2027/index.html) |

> Your challenge must be **approved by the instructor** before you start.
> If you have not received approval yet, contact the instructor by email this week.

---

## 2. Getting started

1. **Register** for your challenge on its official page (team registration, data
   agreement / licence if required) and download the data.
2. **Send your GitHub username**, student ID and chosen challenge to the instructor
   (groups: every member sends their own username and the group's member list).
3. **Accept the invitation** to the `bm5201-2026` organization (check your email or
   [github.com/notifications](https://github.com/notifications)).
4. **Create your repository inside the organization**, or transfer an existing one
   (see section 3).

---

## 3. Your repository

**Name format** (**private** repository):

| Work type | Repository name | Example |
|-----------|-----------------|---------|
| Individual | `{STUDENT_ID}_BM5201` | `21512345_BM5201` |
| Group | `{STUDENT_ID1}_{STUDENT_ID2}_BM5201` — **every member's student ID**, in ascending order | `21512345_21598765_BM5201` |

- Groups use **one shared repository**; the owner adds every member with **Write** access.
- List all members (name + student ID) at the top of your README.
- Each member must have **meaningful commits**; contributions are checked in *Insights → Contributors*.

**If you already have a repository under your own account**, move it into the organization
(commits and history are kept, the old link redirects):
1. Accept the organization invitation first.
2. Repo → **Settings → General → Danger Zone → Transfer ownership**.
3. Choose **Specify an organization** → `bm5201-2026`, confirm, and rename it to the format above.
   Groups: check that all members still have **Write** access.
4. Update your local clone:
   ```bash
   git remote set-url origin https://github.com/bm5201-2026/<your-repo-name>.git
   ```

> Repositories outside the organization will **not** be evaluated.

### Required structure

```
<your-repo-name>/
├── README.md                          ← members, challenge, task, data, how to run, results table
├── requirements.txt                   ← Python packages (with versions)
├── .gitignore                         ← must exclude data/ and model checkpoints
├── assignment1_eda_baseline.ipynb     ← Assignment 1
├── assignment2_solution.ipynb         ← Assignment 2
├── src/
│   ├── __init__.py
│   ├── data.py                        ← loading & preprocessing
│   ├── features.py                    ← feature extraction / embeddings
│   ├── models.py                      ← baselines & proposed model
│   ├── evaluate.py                    ← official metric(s) / scorer wrapper
│   └── utils.py
├── configs/                           ← hyperparameters, experiment settings
├── results/                           ← metric tables (CSV/JSON), small figures
└── data/                              ← NOT committed (task licences + file size)
```

- **Do not commit** the challenge data, audio/image files or large model weights.
  Explain in your README how to obtain them.
- Notebooks tell the story (analysis, plots, discussion); reusable code lives in `src/`.
- Fix random seeds and report them, so your results can be reproduced.

---

## 4. Assignment 1 – EDA & Baseline (5 %)

**File:** `assignment1_eda_baseline.ipynb`
Carry out an exploratory data analysis of your challenge's data and implement baseline models.

| # | Section | What we expect |
|---|---------|----------------|
| 1 | Task definition | Task, input/output, label set, official evaluation metric(s), data splits |
| 2 | Data overview | Size of each split, modalities (text / image / audio), label distribution, missing or noisy samples |
| 3 | Exploratory data analysis | Class balance, length / duration statistics, co-occurring labels, examples per class, language or domain properties — **every plot followed by a written interpretation** |
| 4 | Preprocessing | Cleaning, tokenisation / feature extraction, normalisation — and **why** |
| 5 | Baselines | At least **two** baselines: a trivial one (majority / random) and a standard one (e.g. TF-IDF + linear model, pretrained embeddings + classifier, or the **official task baseline**) |
| 6 | Evaluation | Scores on the **development set** with the **official metric / scorer**, in one results table |
| 7 | Error analysis & next steps | Where the baselines fail, and your plan for Assignment 2 |

---

## 5. Assignment 2 – Proposed Solution (15 %)

**File:** `assignment2_solution.ipynb`
Implement and evaluate your own solution and compare it against the baselines from Assignment 1.

| # | Section | What we expect |
|---|---------|----------------|
| 1 | Motivation | What weakness of the baselines your method addresses, with related work (cited) |
| 2 | Method | Clear description of your model / pipeline (a diagram is welcome) |
| 3 | Experimental setup | Splits, hyperparameters, hardware, seeds, training time |
| 4 | Results | Comparison table: **baselines vs. your solution** on the same split and metric |
| 5 | Ablation | At least one ablation (remove / change one component) |
| 6 | Error analysis | Qualitative examples of successes and failures |
| 7 | Official submission | If the challenge's evaluation phase is open: your submission and score (screenshot in `results/`) |
| 8 | Conclusion | Findings, limitations, future work |

> **Bonus:** a short **system description paper** in the challenge's official format
> (e.g. SemEval / ICASSP template) is strongly encouraged.

---

## 6. How to submit

1. **Restart & Run All**, then commit the notebook **with outputs saved**.
2. Push and create a **tag** before the deadline:
   ```bash
   git add .
   git commit -m "Assignment 1: EDA and baseline"
   git tag assignment1          # assignment2 for Assignment 2
   git push origin main --tags
   ```
3. The **tagged version** is evaluated. Commits after the deadline are not considered.

---

## 7. Evaluation

**Assignment 1 (5 %)**

| Criterion | Points |
|-----------|-------:|
| Task, metric & data overview | 15 |
| EDA with written interpretation | 30 |
| Preprocessing decisions justified | 10 |
| Baselines implemented correctly | 25 |
| Evaluation with official metric + error analysis | 15 |
| Code quality, structure & README | 5 |
| **Total** | **100** |

**Assignment 2 (15 %)**

| Criterion | Points |
|-----------|-------:|
| Motivation & related work | 10 |
| Method (clarity and originality) | 25 |
| Experimental setup & reproducibility | 15 |
| Results vs. baselines | 20 |
| Ablation & error analysis | 20 |
| Code quality, structure & README | 10 |
| **Total** | **100** |

Feedback is given as a **GitHub Issue** in your repository.

---

## 8. Academic integrity

- You may use the **official baseline** and published code / pretrained models, but you must
  **cite every source** (paper, repository, model card) in a markdown cell and in your README.
- Copying code without citation, or presenting someone else's system as your own, is plagiarism.
- Use of generative AI tools must be **declared** in your README (which tool, for what).
- Your commit history must show your work developing over time.
- You may be asked to **explain any part** of your code or results orally.

---

## 9. Important dates

| Assignment | Weight | Deadline |
|------------|-------:|----------|
| **Assignment 1 – EDA & Baseline** | 5 % | **3rd week of November 2026** |
| **Assignment 2 – Proposed Solution** | 15 % | **4th week of December 2026** |

**Questions?** Open an issue in your repository or contact the instructor.
