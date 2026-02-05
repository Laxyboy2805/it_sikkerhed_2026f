# it_sikkerhed_2026f

Dette er et skole projekt for Zealand Næstved

## Opgave 2 - Python unit test
Her er et billede af min unit-tests: 

<img width="2048" height="1226" alt="Skærmbillede 2026-02-03 kl  11 18 12" src="https://github.com/user-attachments/assets/ac624e3f-574e-4370-a529-196e0b00e8cd" />

## Grænsetestværdier 

### emne: Login- og brugerhåndteringssystem med multifactor Auth (Two-Factor Authentication med password og godkendelse gennem mobil)

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

## Ækvivalens klasser 

I et login-system behandles mange forskellige inputs ens. Derfor kan de opdeles i ækvivalensklasser.

Nedenfor er der angivet de forskellige ækvivalens klasser gældende for dette login system: 

Klasse 1 – Gyldige inputs
Alle emails og passwords der overholder reglerne behandles ens, hvor login ville være tilladt.
Eksempler herpå:

test@mail.com / Correct123
user@site.dk / MyPass99

Klasse 2 – Forkert password
Uanset hvilket forkert password der skrives, gør systemet det samme, altså at afvise.

Klasse 3 – Ugyldigt email format
Alle emails der ikke matcher format behandles ens, som vil blive afvist.
Eksempler:
testmail.com
@mail.com
test@

Klasse 4 – Tomme felter
Om det er email eller password der mangler, gør systemet det samme.
Eksempler:
"" / Correct123
test@mail.com / ""

## Cycle proces ved login

LOGGED_OUT
  ↓
ENTER_CREDENTIALS
  ↓ (korrekt)
AUTHENTICATED  ─────────────→ LOGGED_OUT (logout)

ENTER_CREDENTIALS
  ↓ (forkert)
FAILED_ATTEMPT
  ↓ (forsøg < 5)
ENTER_CREDENTIALS   (retry)

FAILED_ATTEMPT
  ↓ (forsøg = 5)
LOCKED
  ↓ (reset)
RESET_PASSWORD
  ↓
LOGGED_OUT

