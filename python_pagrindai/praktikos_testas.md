# Praktikos testas (practice test)

Each question asks: **Ką išspausdins programa?** (What will the program print?) Answers are at the end.

---

## 1 dalis

**1.**
```python
print(7//2, 7%2)
```
A) `3.5 1`  B) `4 1`  C) `3 1`  D) `3 0`

**2.**
```python
s="Python"
print(s[1:4])
```
A) `Pyt`  B) `yth`  C) `ytho`  D) `yt`

**3.**
```python
a=[1,2]
b=a
b.append(3)
print(a)
```
A) `[1, 2]`  B) `[3]`  C) Klaida  D) `[1, 2, 3]`

**4.** Kas įvyks paleidus šią eilutę?
```python
x=int("3.5")
```
A) `x` bus 3  B) `ValueError`  C) `TypeError`  D) `x` bus 4

---

## 2 dalis

**5.**
```python
for i in range(6):
    if i==2: continue
    if i==4: break
    print(i,end=" ")
```
A) `0 1 3`  B) `0 1`  C) `0 1 3 5`  D) `0 1 2 3`

**6.**
```python
def f(x):
    print(x*2)
r=f(5)
print(r)
```
A) `10` ir `10`  B) `10` ir `None`  C) tik `None`  D) Klaida

**7.**
```python
k={'a':1}
print(k.get('b'))
```
A) `KeyError`  B) `0`  C) `None`  D) `b`

**8.**
```python
x=3.14159
print(f"{x:.2f} ir {x>3}")
```
A) `3.14 ir True`  B) `3.14159 ir True`  C) `{x:.2f} ir {x>3}`  D) `3.1 ir 1`

---

## 3 dalis

**9.**
```python
print(bool("0"), bool(""))
```
A) `False False`  B) `True False`  C) `False True`  D) `True True`

**10.** Įvesta `abc`.
```python
try:
    x=int(input())
except ValueError:
    print("A")
else:
    print("B")
finally:
    print("C")
```
A) `A`  B) `A` ir `C`  C) `A`, `B` ir `C`  D) `B` ir `C`

**11.**
```python
x=10
def f():
    x=5
    return x
print(f(), x)
```
A) `5 5`  B) `10 10`  C) `5 10`  D) Klaida

**12.**
```python
print([x*2 for x in range(4) if x%2==0])
```
A) `[0, 4]`  B) `[0, 2, 4, 6]`  C) `[2, 6]`  D) `[0, 4, 8]`

---

## Atsakymai (answers)

| Nr. | Atsakymas | Kodėl |
|---|---|---|
| 1 | C) `3 1` | `//` yra **sveikoji dalyba** (floor division) ir atmeta trupmeninę dalį: 7//2 yra 3. `/` duotų 3.5. `%` yra **liekana** (remainder): 7%2 yra 1. |
| 2 | B) `yth` | **Pjūvis** (slice) `[1:4]` paima indeksus 1, 2 ir 3. Pabaiga (4) neįtraukiama. |
| 3 | D) `[1, 2, 3]` | `b=a` nekopijuoja sąrašo. Abu vardai rodo į tą patį objektą (**nuoroda**, reference), todėl `b.append(3)` pakeičia ir `a`. Kopijai reikia `b=a.copy()`. |
| 4 | B) `ValueError` | Tipas tinka, nes `int()` priima `str`. Netinkama yra pati **reikšmė**: `"3.5"` nėra sveikojo skaičiaus užrašas. |
| 5 | A) `0 1 3` | Kai i yra 2, `continue` praleidžia spausdinimą. Kai i yra 4, `break` nutraukia ciklą. |
| 6 | B) `10` ir `None` | `r=f(5)` **iškviečia** (calls) funkciją, ir jos viduje `print` išspausdina 10. Funkcija neturi `return`, todėl grąžina `None`. |
| 7 | C) `None` | `.get()` neranda rakto ir grąžina `None`. Užrašas `k['b']` iškeltų `KeyError`. |
| 8 | A) `3.14 ir True` | `:.2f` palieka du skaičius po kablelio. `x>3` yra **loginis reiškinys** (logical expression), kurio reikšmė `True`. |
| 9 | B) `True False` | `"0"` yra netuščia eilutė, todėl ji **teisinga** (truthy). Tuščia eilutė `""` yra **klaidinga** (falsy). |
| 10 | B) `A` ir `C` | Įvyko `ValueError`, todėl vykdomas `except`. `else` vykdomas tik tada, kai klaidos nėra. `finally` vykdomas visada. |
| 11 | C) `5 10` | `x` funkcijos viduje yra **lokalusis kintamasis** (local variable). Jis nekeičia **globaliojo** (global) `x`. |
| 12 | A) `[0, 4]` | Iš `range(4)` lyginiai yra 0 ir 2. Padauginus iš 2, gaunama 0 ir 4. |

## Atmintinė (cheat sheet)

- **ValueError**: tipas tinka, bet reikšmė netinka (`int("abc")`). **TypeError**: netinka pats tipas (`"a"+1`).
- `print` tik parodo reikšmę ekrane. `return` grąžina reikšmę kvietėjui. Jei funkcija neturi `return`, ji grąžina `None`.
- `k[raktas]`: kai rakto nėra, iškeliama `KeyError`. `k.get(raktas)`: kai rakto nėra, grąžinama `None`.
- `try` / `except` / `else` / `finally`: `else` vykdomas, kai klaidos nebuvo. `finally` vykdomas visada.
