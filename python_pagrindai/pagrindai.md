# Python pagrindai: teorija su lietuviškais terminais

Format: **Lietuviškas terminas** (English term). Code lines end with `# rezultatas` (output) showing what the line prints.

---

## 1. Sintaksė (syntax), įtrauka (indentation), komentaras (comment)

- **Programa** (program) is a sequence of **sakiniai / komandos** (statements) executed top to bottom.
- **Įtrauka** (indentation, 4 spaces) defines a **kodo blokas** (code block). Python has no `{}`; wrong indentation raises `IndentationError`.
- **Komentaras** (comment) starts with `#` and is ignored by the **interpretatorius** (interpreter).

```python
if True:
    print("viduje")   # bloko dalis
print("lauke")
# viduje
# lauke
```

---

## 2. Kintamasis (variable), reikšmė (value), priskyrimas (assignment)

- **Kintamasis** is a name that refers to a **reikšmė**. `=` is **priskyrimo operatorius** (assignment operator), not equality.
- Python is **dinamiškai tipizuota** (dynamically typed): the type belongs to the value, not to the variable.

```python
x=5
x=x+1
print(x)        # 6
a,b=1,2
a,b=b,a         # sukeitimas (swap)
print(a,b)      # 2 1
```

---

## 3. Duomenų tipai (data types)

| Lietuviškai | English | Python | Pavyzdys |
|---|---|---|---|
| sveikasis skaičius | integer | `int` | `5`, `-3` |
| realusis / slankiojo kablelio skaičius | float | `float` | `2.5` |
| simbolių eilutė, eilutė | string | `str` | `"labas"` |
| loginis tipas | boolean | `bool` | `True`, `False` |
| tuščia reikšmė | None | `NoneType` | `None` |
| sąrašas | list | `list` | `[1,2,3]` |
| kortežas | tuple | `tuple` | `(1,2)` |
| žodynas | dictionary | `dict` | `{'a':1}` |
| aibė | set | `set` | `{1,2}` |

```python
print(type(5))       # <class 'int'>
print(type(2.5))     # <class 'float'>
print(type("5"))     # <class 'str'>
```

**Tipo konvertavimas** (type conversion / casting):

```python
print(int("12")+1)   # 13
print(str(12)+"1")   # 121
print(float("2.5"))  # 2.5
print(int(3.9))      # 3        (nukerta, neapvalina)
int("3.5")           # ValueError
int("abc")           # ValueError
```

**Kintamieji** (mutable) types: `list`, `dict`, `set`. **Nekintamieji** (immutable) types: `int`, `float`, `str`, `tuple`, `bool`.

---

## 4. Operatoriai (operators) ir reiškiniai (expressions)

**Aritmetiniai** (arithmetic):

```python
print(7/2)    # 3.5   dalyba (division), visada float
print(7//2)   # 3     sveikoji dalyba (floor division)
print(-7//2)  # -4    apvalina žemyn, ne link nulio
print(7%2)    # 1     liekana (modulo)
print(2**3)   # 8     kėlimas laipsniu (power)
```

**Palyginimo** (comparison): `== != < > <= >=`, which return `bool`.

**Loginiai** (logical): `and` (ir), `or` (arba), `not` (ne).

```python
print(5>3 and 2>4)   # False
print(not True)      # False
print(0 or "x")      # x      or grąžina pirmą teisingą reikšmę
print("" and 5)      #        (tuščia eilutė) and grąžina pirmą klaidingą
```

**Klaidingos reikšmės** (falsy values): `0`, `0.0`, `""`, `[]`, `{}`, `None`, `False`. Every other value is **teisinga** (truthy).

```python
print(bool(""))    # False
print(bool("0"))   # True    netuščia eilutė
print(bool([]))    # False
```

`==` compares values. `is` checks whether two names refer to the same object (tapatumas, identity). Use `is` only with `None`: `if x is None:`.

---

## 5. Įvestis ir išvestis (input / output)

```python
vardas=input("Vardas: ")      # input() VISADA grąžina str
amzius=int(input("Amzius: ")) # reikia konvertuoti
print("a","b","c")            # a b c
print("a","b",sep="-")        # a-b
print("a",end="");print("b")  # ab
print(f"{vardas} turi {amzius} m.")   # f-eilutė (f-string)
print(f"{3.14159:.2f}")       # 3.14
```

---

## 6. Eilutės (strings)

- **Indeksas** (index) starts at 0. A negative index counts from the end.
- **Pjūvis** (slice) `[pradžia:pabaiga:žingsnis]`. The end position is **neįtraukiama** (not included).

```python
s="Python"
print(s[0])      # P
print(s[-1])     # n
print(s[1:3])    # yt
print(s[:2])     # Py
print(s[::-1])   # nohtyP     apvertimas (reverse)
print(len(s))    # 6
print(s.upper()) # PYTHON
print(s.lower()) # python
print("  a b ".strip())       # a b
print("a,b,c".split(","))     # ['a', 'b', 'c']
print("-".join(["a","b"]))    # a-b
print(s.replace("P","J"))     # Jython
print("th" in s)              # True
s[0]="J"                      # TypeError: eilutės nekintamos
```

---

## 7. Sąlyginis sakinys (conditional statement)

```python
taskai=75
if taskai>=90:
    print("Puikiai")
elif taskai>=50:
    print("Islaikyta")
else:
    print("Neislaikyta")
# Islaikyta
```

Only the **first** branch whose condition is true runs.

**Sąlyginis reiškinys** (ternary expression):

```python
x=-3
zenklas="teigiamas" if x>0 else "neteigiamas"
print(zenklas)   # neteigiamas
```

---

## 8. Ciklai (loops)

**`for` ciklas** iterates over a **seka** (sequence). **Iteracija** (iteration) is one pass through the loop.

```python
for i in range(3):        # 0,1,2      (pabaiga neįtraukiama)
    print(i,end=" ")      # 0 1 2
for i in range(1,10,3):
    print(i,end=" ")      # 1 4 7
for raide in "abc":
    print(raide,end=" ")  # a b c
for i,v in enumerate(["x","y"]):
    print(i,v)            # 0 x   /   1 y
```

**`while` ciklas** repeats while the **sąlyga** (condition) is true:

```python
n=3
while n>0:
    print(n,end=" ")
    n-=1
# 3 2 1
```

**Ciklo valdymas** (loop control):
- `break` stops the loop completely (nutraukia ciklą).
- `continue` skips to the next iteration (pereina prie kitos iteracijos).

```python
for i in range(6):
    if i==2: continue
    if i==4: break
    print(i,end=" ")
# 0 1 3
```

**Begalinis ciklas** (infinite loop): `while True:` combined with `break`.

---

## 9. Sąrašas (list)

An ordered, changeable collection of **elementai** (elements).

```python
s=[3,1,2]
s.append(5)       # prideda į galą    [3, 1, 2, 5]
s.insert(0,9)     # įterpia           [9, 3, 1, 2, 5]
s.remove(1)       # pašalina reikšmę  [9, 3, 2, 5]
x=s.pop()         # pašalina paskutinį, x=5   [9, 3, 2]
s.sort()          # rikiuoja vietoje  [2, 3, 9]
print(sorted([3,1,2]))  # [1, 2, 3]    naujas sąrašas
print(len(s),sum(s),max(s),min(s))   # 3 14 9 2
print(2 in s)     # True
```

**Spąstai** (trap): assignment does not copy a list.

```python
a=[1,2]
b=a          # ta pati nuoroda (reference)
b.append(3)
print(a)     # [1, 2, 3]
c=a.copy()   # tikra kopija (copy)
```

**Sąrašų generatorius** (list comprehension):

```python
kvadratai=[x**2 for x in range(5)]
print(kvadratai)                       # [0, 1, 4, 9, 16]
lyginiai=[x for x in range(10) if x%2==0]
print(lyginiai)                        # [0, 2, 4, 6, 8]
```

---

## 10. Kortežas (tuple) ir aibė (set)

- **Kortežas** (tuple) is an ordered collection that cannot be changed.
- **Aibė** (set) has no duplicates and no order.

```python
t=(1,2,3)
print(t[0])        # 1
t[0]=5             # TypeError
a={1,2,2,3}
print(a)           # {1, 2, 3}
print({1,2}&{2,3}) # {2}        sankirta (intersection)
print({1,2}|{2,3}) # {1, 2, 3}  sąjunga (union)
```

---

## 11. Žodynas (dictionary)

Stores **raktas : reikšmė** (key : value) pairs. Keys are unique.

```python
k={'pavadinimas':'Dune','metai':1965}
print(k['metai'])              # 1965
k['metai']=1966                # keičia reikšmę
k['autorius']='Herbert'        # prideda naują raktą
print(k.get('dydis'))          # None    nėra rakto, klaidos nėra
print(k['dydis'])              # KeyError
print('metai' in k)            # True    tikrina RAKTUS
for raktas,reiksme in k.items():
    print(raktas,reiksme)
print(list(k.keys()))          # ['pavadinimas', 'metai', 'autorius']
nauja={**k,'metai':2000}       # kopija su pakeitimu
```

---

## 12. Funkcija (function)

- **Apibrėžimas** (definition) uses `def`. **Iškvietimas** (call) runs it.
- **Parametras** (parameter) is the name in the definition. **Argumentas** (argument) is the value you pass in.
- `return` gives back the **grąžinama reikšmė** (return value). A function without `return` returns `None`.

```python
def suma(a,b=0):          # b - numatytoji reikšmė (default value)
    return a+b
print(suma(2,3))          # 5
print(suma(2))            # 2
print(suma(b=1,a=4))      # 5    vardiniai argumentai (keyword arguments)

def sveikinti(vardas):
    print("Labas,",vardas)
r=sveikinti("Jonas")      # Labas, Jonas
print(r)                  # None
```

**Spąstai**: `print` shows a value on screen; `return` hands a value back to the caller. They are different things.

**Kintamojo matomumo sritis** (variable scope):
- **Lokalusis kintamasis** (local variable) exists only inside its function.
- **Globalusis kintamasis** (global variable) is defined outside any function.

```python
x=10
def f():
    x=5        # naujas lokalus x
    return x
print(f(),x)   # 5 10
```

**Rekursija** (recursion) is a function calling itself:

```python
def faktorialas(n):
    return 1 if n<=1 else n*faktorialas(n-1)
print(faktorialas(5))   # 120
```

**Lambda funkcija** (anonymous function):

```python
print(sorted(["bbb","a","cc"],key=lambda z:len(z)))   # ['a', 'cc', 'bbb']
```

---

## 13. Išimtys (exceptions) ir klaidų valdymas (error handling)

Common errors:

| Klaida | Kada |
|---|---|
| `SyntaxError` | sintaksės klaida (bad syntax) |
| `ValueError` | netinkama reikšmė: `int("abc")` |
| `TypeError` | netinkamas tipas: `"a"+1` |
| `IndexError` | indeksas už ribų (index out of range) |
| `KeyError` | nėra rakto (missing key) |
| `ZeroDivisionError` | dalyba iš nulio |
| `NameError` | neapibrėžtas kintamasis |

```python
try:
    x=int(input("Skaicius: "))
except ValueError as klaida:
    print("Klaida:",klaida)       # vyksta, jei įvyko klaida
else:
    print("Gerai:",x)             # vyksta, jei klaidos NEBUVO
finally:
    print("Visada")               # vyksta visada
```

With input `abc`, the output is:
```
Klaida: invalid literal for int() with base 10: 'abc'
Visada
```

**Išimties iškėlimas** (raising an exception):

```python
def tikrinti(amzius):
    if amzius<0:
        raise ValueError("Amzius negali buti neigiamas")
```

---

## 14. Moduliai (modules) ir importavimas (import)

```python
import math
print(math.sqrt(16))      # 4.0
from random import randint
print(randint(1,6))       # atsitiktinis skaičius 1-6
import logging            # žurnalizavimas (logging)
```

**Žurnalo lygiai** (log levels), from lowest to highest: `DEBUG < INFO < WARNING < ERROR < CRITICAL`. With level `INFO`, `DEBUG` messages are not written.

---

## 15. Failai (files)

```python
with open("a.txt","w",encoding="utf-8") as f:   # "w" rašyti (perrašo), "a" papildyti, "r" skaityti
    f.write("labas\n")
with open("a.txt","r",encoding="utf-8") as f:
    print(f.read())       # labas
```

`with` closes the file automatically (automatiškai uždaro).

---

## 16. Klasė (class) ir objektas (object), basic level only

- **Klasė** (class) is a template. **Objektas / egzempliorius** (object / instance) is one thing made from that template.
- **Atributas** (attribute) is data stored in the object. **Metodas** (method) is a function that belongs to the object.
- **Konstruktorius** (constructor) is `__init__`. `self` refers to the object itself.

```python
class Knyga:
    def __init__(self,pavadinimas):
        self.pavadinimas=pavadinimas
    def rodyti(self):
        return f"Knyga: {self.pavadinimas}"
k=Knyga("Dune")
print(k.rodyti())    # Knyga: Dune
```

---

## 17. Dažni egzamino spąstai (common exam traps)

```python
print(0.1+0.2==0.3)   # False   (slankiojo kablelio paklaida)
print(round(2.5))     # 2       (apvalina iki lyginio)
print(round(3.5))     # 4
print("3"*3)          # 333
print([0]*3)          # [0, 0, 0]
print(10/5)           # 2.0     (ne 2)
print(len([[1,2],[3]]))   # 2
print("abc"<"abd")    # True    (lygina simbolis po simbolio)
x=[1,2,3]
print(x[5])           # IndexError
print(x[1:10])        # [2, 3]  (pjūvis klaidos nemeta)
```

---

## Žodynėlis (glossary)

| Lietuviškai | English |
|---|---|
| kintamasis | variable |
| reikšmė | value |
| priskyrimas | assignment |
| duomenų tipas | data type |
| sveikasis skaičius | integer |
| realusis skaičius | float |
| simbolių eilutė | string |
| loginis tipas | boolean |
| reiškinys | expression |
| sakinys / komanda | statement |
| sąlyga | condition |
| sąlyginis sakinys | if statement |
| ciklas | loop |
| iteracija | iteration |
| sąrašas | list |
| kortežas | tuple |
| žodynas | dictionary |
| raktas | key |
| aibė | set |
| elementas | element / item |
| indeksas | index |
| pjūvis | slice |
| funkcija | function |
| parametras | parameter |
| argumentas | argument |
| grąžinama reikšmė | return value |
| numatytoji reikšmė | default value |
| matomumo sritis | scope |
| lokalusis / globalusis | local / global |
| rekursija | recursion |
| išimtis | exception |
| klaidų valdymas | error handling |
| iškelti išimtį | raise an exception |
| modulis | module |
| importuoti | import |
| klasė | class |
| objektas / egzempliorius | object / instance |
| metodas | method |
| atributas | attribute |
| konstruktorius | constructor |
| įvestis / išvestis | input / output |
| įtrauka | indentation |
| komentaras | comment |
| tipo konvertavimas | type conversion |
| kintamas / nekintamas tipas | mutable / immutable |
| nuoroda | reference |
| žurnalas, žurnalizavimas | log, logging |
| interpretatorius | interpreter |
| algoritmas | algorithm |
| derinimas (klaidų paieška) | debugging |
