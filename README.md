# it_sikkerhed_2026f

Dette er et skole projekt for Zealand Næstved

## Opgave 2 - Python unit test
Her er et billede af min unit-tests: 

<img width="2048" height="1226" alt="Skærmbillede 2026-02-03 kl  11 18 12" src="https://github.com/user-attachments/assets/ac624e3f-574e-4370-a529-196e0b00e8cd" />

## Grænsetestværdier 

### emne: login og password 

Der testes om at en password har en længde af mindst 8 tegn, da det ellers ville være for kort og nemt at gætte. 

Her er betingelsen defineret i en funktion: 
def is_valid_password(password: str) -> bool:
    return len(password) >= 8

Her testes forskellige scenarioer: 

For kort
assert is_valid_password("Ab1!") == False  # 4 tegn

Lige under grænsen
assert is_valid_password("Abc12!@") == False  # 7 tegn

På grænsen (minimum)
assert is_valid_password("Abc123!@") == True  # 8 tegn

Over grænsen
assert is_valid_password("Abc1234!@") == True  # 9 tegn
