# Test Cases – LLM Text Analysis System

This file contains example inputs and expected behaviors for validating prompt consistency.

---

## Test Case 1 – Standard multi-sentence text

### Input
[Wczoraj złożyłem reklamację słuchawek zakupionych 10 listopada. 
Dziś otrzymałem odpowiedź, że serwis potrzebuje numeru seryjnego, którego nie mam pod ręką. 
Napisałem do sklepu, że mogę dosłać numer w piątek po powrocie do domu. 
Poprosiłem również o potwierdzenie, że termin rozpatrzenia reklamacji zostanie wstrzymany do czasu uzupełnienia danych.]

### Expected Behavior
- Output must follow the fixed structure (Summary + Chronology).
- Summary must be concise, formal, and based only on the input.
- Chronology must be numerically indexed and reflect the input’s sequence.
- No new facts, no topic changes, no abstractions.

---

## Test Case 2 – Short but valid text

### Input
[W poniedziałek wysłałem dokumenty do działu HR. We wtorek poproszono mnie o uzupełnienie brakującego załącznika.]

### Expected Behavior
- Output must follow the fixed structure.
- Summary should remain concise (no unnecessary expansion).
- Chronology should contain only key points supported by the input.

---

## Test Case 3 – Text with minor linguistic errors

### Input
[Dnia 5 grudnia wysłałem paczke do serwisu. 
Dostałem maila że brakuje formularza zwrotu, więc dosłałem go tego samego dnia. 
Prosze o potwierdzenie przyjęcia dokumentów.]

### Expected Behavior
- Output must follow the fixed structure.
- Summary and Chronology must preserve meaning.
- Minor linguistic errors may be corrected without changing factual content.
- No invented details.

---

## Edge Case 1 – Minimum valid input (one complete sentence)

### Input
[Klient zgłosił problem z fakturą i poprosił o korektę danych.]

### Expected Behavior
- Output must still follow the fixed structure.
- Chronology may contain a single numbered point if appropriate.
- No added context beyond the input.

---

## Edge Case 2 – Insufficient input (should trigger fallback)

### Input
[Reklamacja. Pilne.]

### Expected Behavior
- The system must return exactly the fallback message defined in the prompt.
