# Test Cases – LLM Text Analysis System

This document contains example inputs and expected behaviors used to validate
the consistency, determinism, and constraint adherence of the text analysis prompt.

---

## Test Case 1 – Standard multi-sentence text

### Input
Wczoraj złożyłem reklamację słuchawek zakupionych 10 listopada. 
Dziś otrzymałem odpowiedź, że serwis potrzebuje numeru seryjnego, którego nie mam pod ręką. 
Napisałem do sklepu, że mogę dosłać numer w piątek po powrocie do domu. 
Poprosiłem również o potwierdzenie, że termin rozpatrzenia reklamacji zostanie wstrzymany do czasu uzupełnienia danych.

### Expected Behavior
- The output must follow the fixed structure defined in the prompt.
- The summary must be concise, formal, and strictly based on the input text.
- The chronology must be numerically indexed and reflect the original sequence of events.
- No new facts, assumptions, or abstractions may be introduced.

---

## Test Case 2 – Short but valid text

### Input
W poniedziałek wysłałem dokumenty do działu HR. 
We wtorek poproszono mnie o uzupełnienie brakującego załącznika.

### Expected Behavior
- The output must follow the fixed structure.
- The summary should remain concise without unnecessary expansion.
- The chronology should include only the key points supported by the input.

---

## Test Case 3 – Text with minor linguistic errors

### Input
Dnia 5 grudnia wysłałem paczke do serwisu. 
Dostałem maila że brakuje formularza zwrotu, więc dosłałem go tego samego dnia. 
Prosze o potwierdzenie przyjęcia dokumentów.

### Expected Behavior
- The output must follow the fixed structure.
- Minor linguistic errors may be corrected if they do not alter the factual meaning.
- The original intent and factual content must be preserved.
- No invented details are allowed.

---

## Edge Case 1 – Minimum valid input (one complete sentence)

### Input
Klient zgłosił problem z fakturą i poprosił o korektę danych.

### Expected Behavior
- The output must still follow the fixed structure.
- The chronology may consist of a single numbered point if appropriate.
- No additional context may be added beyond the input.

---

## Edge Case 2 – Insufficient input (fallback case)

### Input
Reklamacja. Pilne.

### Expected Behavior
- The system must return exactly the fallback message defined in the prompt.
- No summary or chronology should be generated.
