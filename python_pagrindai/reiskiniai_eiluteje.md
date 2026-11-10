# Reiškiniai eilutės viduje (expressions inside a string)

The main tool is the **f-eilutė** (f-string, short for formatted string literal). Put `f` before the opening quote. Anything inside `{}` is evaluated as Python code, and its result is inserted into the text.

## 1. Kintamieji (variables)

```python
vardas="Jonas"
amzius=20
print(f"{vardas} turi {amzius} metu")    # Jonas turi 20 metu
```

## 2. Skaičiavimai (calculations)

```python
a=7
b=2
print(f"{a}+{b}={a+b}")       # 7+2=9
print(f"{a}/{b}={a/b}")       # 7/2=3.5
print(f"Kvadratas: {a**2}")   # Kvadratas: 49
```

## 3. Funkcijų ir metodų iškvietimai (function and method calls)

```python
s="python"
print(f"{s.upper()} turi {len(s)} raides")   # PYTHON turi 6 raides
k={'pavadinimas':'Dune','metai':1965}
print(f"{k['pavadinimas']} ({k['metai']})")   # Dune (1965)
```

Kabutės (quotes) inside `{}` must differ from the outer quotes. In Python 3.12 and newer, the same quotes are also allowed.

## 4. Sąlyginis reiškinys (conditional expression)

```python
pasiskolinta=True
print(f"Statusas: {'Pasiskolinta' if pasiskolinta else 'Laisva'}")   # Statusas: Pasiskolinta
```

## 5. Formatavimas (formatting) after `:`

```python
x=3.14159
print(f"{x:.2f}")          # 3.14        2 skaičiai po kablelio
print(f"{1234567:,}")      # 1,234,567   tūkstančių skyriklis
print(f"{5:03d}")          # 005         užpildymas nuliais
print(f"{0.25:.0%}")       # 25%         procentai
print(f"[{'a':>5}]")       # [    a]     lygiuoti dešinėn
print(f"[{'a':<5}]")       # [a    ]     lygiuoti kairėn
print(f"[{'a':^5}]")       # [  a  ]     centruoti
```

## 6. Derinimas (debugging) with `=`

```python
x=5
print(f"{x=}")       # x=5
print(f"{x*2=}")     # x*2=10
```

## 7. Riestiniai skliaustai (curly braces) as plain text

Write each brace twice, as `{{` and `}}`:

```python
x=5
print(f"{{x}} yra {x}")   # {x} yra 5
```

## 8. Senesni būdai (older methods)

You may still see these on exams:

```python
vardas="Jonas"
amzius=20
print("{} turi {} metu".format(vardas,amzius))   # Jonas turi 20 metu
print("{0} {1} {0}".format("a","b"))             # a b a
print("%s turi %d metu" % (vardas,amzius))       # Jonas turi 20 metu
print("%.2f" % 3.14159)                          # 3.14
print(vardas+" turi "+str(amzius)+" metu")       # sujungimas (concatenation)
```

**Spąstai** (trap): `"turi "+20` raises `TypeError`. A number must be converted with `str()` before you join it to a string. f-strings do this automatically.

## 9. Kodo vykdymas iš eilutės (running code stored in a string)

`eval()` and `exec()` treat a whole string as code:

```python
print(eval("2+3*4"))          # 14      eval apskaičiuoja reiškinį ir grąžina reikšmę
exec("for i in range(3): print(i,end=' ')")   # 0 1 2     exec vykdo sakinius, grąžina None
```

Never use them on text a user typed in. The user could type any code and it would run (saugumo spraga, security hole). In exams and normal programs, use f-strings.

## Santrauka (summary)

| Būdas | Pavyzdys | Rezultatas |
|---|---|---|
| f-eilutė | `f"{2+3}"` | `5` |
| formatavimas | `f"{2/3:.2f}"` | `0.67` |
| `.format()` | `"{}".format(2+3)` | `5` |
| `%` | `"%d" % (2+3)` | `5` |
| sujungimas | `"a"+str(5)` | `a5` |
| `eval()` | `eval("2+3")` | `5` |
