# RAG Corpus Poisoning and Mitigation Lab

## 1. Overview

This project demonstrates a **RAG (Retrieval-Augmented Generation) corpus poisoning attack** against a locally running language model. The experiment tests whether an untrusted document containing false information can influence the model's answer and evaluates source allowlisting as a mitigation.

## 2. Objectives

- Build a basic RAG application using a local LLM.
- Establish a clean baseline using university policy documents.
- Test the effect of adding a poisoned policy document.
- Compare vulnerable and mitigated behaviour.
- Evaluate whether source allowlisting prevents the poisoned document from influencing the answer.

## 3. Tools Used

- Python
- Ollama
- Llama 3.1
- Nomic Embed Text

## 4. Methodology

The experiment was conducted in five stages:

1. **Clean baseline:** The RAG application retrieved information from the original university policy documents.
2. **Controlled poisoning:** A false policy document was added to the corpus and its retrieval was observed.
3. **Repeatability test:** The controlled experiment was repeated five times under clean and poisoned conditions.
4. **Vulnerable attack:** The application was tested with a simple prompt that did not explicitly instruct the model to prioritise trusted sources or resolve conflicting policies.
5. **Mitigation:** Source allowlisting was applied so that only documents from an approved source were included in the retrieval corpus.

## 5. Results

### Vulnerable RAG

The clean corpus produced the correct answer that multi-factor authentication (MFA) was required.

After the poisoned document was added, the application retrieved the false policy and generated an incorrect answer stating that MFA was not required. The generated answer cited the poisoned document.

### Mitigation

Source allowlisting excluded the unapproved poisoned document from the retrieval corpus. The application then returned the correct answer based on the original IT policy.

### Summary

| Test | Observation |
|---|---|
| Clean baseline | Correct policy retrieved and answer generated |
| Controlled poisoning | Poisoned document retrieved, but the defensive prompt preserved the correct answer |
| Repeatability test | No false answers in five poisoned-condition runs with the defensive prompt |
| Vulnerable attack | Poisoned document caused an incorrect answer in the tested scenario |
| Mitigation | Source allowlisting excluded the poisoned document and restored the correct answer |

## 6. Screenshots

### Poisoning Attack

The poisoned document influenced the generated answer, resulting in an incorrect response.

![Poisoning attack result](screenshots/poisoned_attack.png)

### Mitigation Result

After source allowlisting was applied, the poisoned document was excluded and the correct answer was restored.

![Mitigation result](screenshots/remediated_result.png)

## 7. Mitigation Applied

The experiment used **source allowlisting** to restrict retrieval to documents from an approved source.

In a real deployment, source trust should be established through authenticated provenance and a controlled ingestion process. A document should not be trusted merely because it claims to be official.

## 8. Limitations

- The experiment used a small, synthetic university policy corpus.
- Testing focused on a specific MFA-related query.
- The successful vulnerable attack was demonstrated in a single recorded run.
- The repeated evaluation tested a defensive prompt and did not establish that the prompt prevents all poisoning attacks.
- Results may differ with other models, documents, prompts, and retrieval configurations.

The results demonstrate the behaviour of this test setup and should not be interpreted as proof that the mitigation prevents every form of RAG poisoning.

## 9. Running the Lab

Install the required Python dependencies and ensure Ollama is running with the required models available.

Run the experiments from the project directory:

```bash
python app.py
python lab_vulnerable_poisoning.py
python lab_repeatable_evaluation.py
python lab_remediated.py
```

The experiment scripts save their results in the `results/` directory.

## 10. Disclaimer

This project is intended for educational purposes and controlled AI security testing only.
