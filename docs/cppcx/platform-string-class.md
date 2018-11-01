---
title: Platform::String, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: ef9838fa8a6a34eac1d2d3531ff93fb124c81d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607036"
---
# <a name="platformstring-class"></a>Platform::String, classe

Représente une collection séquentielle de caractères Unicode utilisée pour représenter du texte. Pour plus d’informations et des exemples, consultez [chaînes](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterators

Deux fonctions d'itérateur, qui ne sont pas membres de la classe String, peuvent être utilisées avec la fonction de modèle `std::for_each` pour énumérer les caractères d'un objet String.

|Membre|Description|
|------------|-----------------|
|`const char16* begin(String^ s)`|Retourne un pointeur au début de l'objet String spécifié.|
|`const char16* end(String^ s)`|Retourne un pointeur après la fin de l'objet String spécifié.|

### <a name="members"></a>Membres

La classe String hérite de la classe Object et des interfaces IDisposable, IEquatable et IPrintable.

La classe String a également les types de membres ci-dessous.

**Constructeurs**

|Membre|Description|
|------------|-----------------|
|[String::String](#ctor)|Initialise une nouvelle instance de la classe String.|

**Méthodes**

La classe String hérite des méthodes Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() et ToString() de la [Platform::Object Class](../cppcx/platform-object-class.md). La classe String contient également les méthodes ci-dessous.

|Méthode|Description|
|------------|-----------------|
|[String::BEGIN](#begin)|Retourne un pointeur au début de la chaîne actuelle.|
|[String::CompareOrdinal](#compareordinal)|Compare deux objets `String` en évaluant les valeurs numériques des caractères correspondants dans les deux valeurs de chaîne représentées par les objets.|
|[String::Concat](#concat)|Concatène les valeurs de deux objets String.|
|[String::Data](#data)|Retourne un pointeur au début de la chaîne actuelle.|
|[String::dispose](#dispose)|Libère des ressources.|
|[String::end](#end)|Retourne un pointeur après la fin de la chaîne actuelle.|
|[String::Equals](#equals)|Indique si l'objet spécifié est égal à l'objet actif.|
|[String::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|
|[String::IsEmpty](#isempty)|Indique si l'objet String actuel est vide.|
|[String::IsFastPass](#isfastpass)|Indique si l’objet String actuel participe à une *passage rapide* opération. Dans une opération de passage rapide, le comptage des références est interrompu.|
|[String::Length](#length)|Récupère la longueur de l'objet String en cours.|
|[String::ToString](#tostring)|Retourne un objet String dont la valeur est identique à celle de la chaîne en cours.|

**Opérateurs**

La classe String a les opérateurs suivants.

|Membre|Description|
|------------|-----------------|
|[String::operator ==, opérateur](#operator-equality)|Indique si deux objets String spécifiés ont la même valeur.|
|[Opérateur opérateur+](#operator-plus)|Concatène deux objets String en un nouvel objet String.|
|[String::operator > opérateur](#operator-greater-than)|Indique si la valeur d'un objet String est supérieure à la valeur d'un deuxième objet String.|
|[String::operator > =, opérateur](#operator-greater-than-or-equals)|Indique si la valeur d'un objet String est supérieure ou égale à la valeur d'un deuxième objet String.|
|[String::operator ! =, opérateur](#operator-inequality)|Indique si deux objets String spécifiés ont des valeurs différentes.|
|[String::operator < opérateur](#operator-less-than)|Indique si la valeur d'un objet String est inférieure à la valeur d'un deuxième objet String.|

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**En-tête** vccorlib.h (inclus par défaut)

## <a name="begin"></a>  String::BEGIN, méthode

Retourne un pointeur au début de la chaîne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
char16* Begin();
```

### <a name="return-value"></a>Valeur de retour

Pointeur au début de la chaîne actuelle.

## <a name="compareordinal"></a>  String::CompareOrdinal, méthode

Compare deux objets `String` en évaluant les valeurs numériques des caractères correspondants dans les deux valeurs de chaîne représentées par les objets.

### <a name="syntax"></a>Syntaxe

```cpp
int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet String.

*str2*<br/>
Deuxième objet String.

### <a name="return-value"></a>Valeur de retour

Entier qui indique la relation lexicale entre les deux comparateurs. Le tableau ci-dessous répertorie les valeurs de retour possibles.

|Value|Condition|
|-----------|---------------|
|-1|`str1` est inférieur à `str2`.|
|0|`str1` est égal à `str2`.|
|1|`str1` est supérieur à `str2`.|

## <a name="concat"></a>  String::concat, méthode

Concatène les valeurs de deux objets String.

### <a name="syntax"></a>Syntaxe

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet String ou `null`.

*str2*<br/>
Deuxième objet String ou `null`.

### <a name="return-value"></a>Valeur de retour

Nouvel objet String^ dont la valeur est la concaténation des valeurs de `str1` et `str2`.

Si `str1` est `null` et `str2` ne l’est pas, `str1`est retourné. Si `str2` est `null` et `str1` ne l’est pas, `str2`est retourné. Si `str1` et `str2` sont tous deux `null`, la chaîne vide (L"") est retournée.

## <a name="data"></a>  String::Data, méthode

Retourne un pointeur vers le début de la mémoire tampon de données de l'objet en tant que tableau de style C d'éléments `char16` (`wchar_t`).

### <a name="syntax"></a>Syntaxe

```
const char16* Data();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le début d’un `const char16` tableau de caractères Unicode (`char16` est un typedef pour `wchar_t`).

### <a name="remarks"></a>Notes

Utilisez cette méthode pour convertir de `Platform::String^` en `wchar_t*`. Lorsque l'objet `String` se trouve hors de portée, la validité du pointeur donnée n'est plus garantie. Pour stocker les données allant au-delà de la durée de vie de l’original `String` de l’objet, utilisez [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) pour copier le tableau dans la mémoire que vous avez allouée à vous-même.

## <a name="dispose"></a>  String::dispose, méthode

Libère des ressources.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override void Dispose();
```

## <a name="end"></a>  String::end, méthode

Retourne un pointeur après la fin de la chaîne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
char16* End();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers au-delà de la fin de la chaîne actuelle.

### <a name="remarks"></a>Notes

End() retourne Begin() + Length.

## <a name="equals"></a>  String::Equals, méthode

Indique si la chaîne spécifiée a la même valeur que l'objet actif.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si `str` est égal à l’objet actuel ; sinon, **false**.

### <a name="remarks"></a>Notes

Cette méthode est équivalente à la [String::CompareOrdinal](#compareordinal). Dans la première surcharge, il est attendu que le paramètre `str` puisse être casté en un objet String^.

## <a name="gethashcode"></a>  String::GetHashCode, méthode

Retourne le code de hachage de cette instance.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Valeur de retour

Code de hachage de cette instance.

## <a name="isempty"></a>  String::IsEmpty, méthode

Indique si l'objet String actuel est vide.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Valeur de retour

**true** si actuel `String` objet est **null** ou une chaîne vide (L » ") ; sinon, **false**.

## <a name="isfastpass"></a>  String::isfastpass, méthode

Indique si l’objet String actuel participe à une *passage rapide* opération. Dans une opération de passage rapide, le comptage des références est interrompu.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Valeur de retour

**true** si actuel `String` objet est passage rapide ; sinon, **false**.

### <a name="remarks"></a>Notes

Au cours d'un appel de fonction où un objet, dont les références sont comptabilisées, constitue un paramètre, et que la fonction appelée ne lit que cet objet, le compilateur peut sans risque interrompre le décompte de références et améliorer les performances d'appel. Votre code ne peut rien faire d'utile avec cette propriété. Le système gère tous les détails.

## <a name="length"></a>  String::Length, méthode

Récupère le nombre de caractères dans le courant `String` objet.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères dans le courant `String` objet.

### <a name="remarks"></a>Notes

La longueur d'une chaîne sans caractères est zéro. La longueur de la chaîne suivante est 5 :

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Le tableau de caractères retourné par la [String::Data](#data) a un caractère supplémentaire, qui est le caractère NULL ou « \0 ». La longueur de ce caractère est également de deux octets.

## <a name="operator-plus"></a>  String::operator +, opérateur

Concatène deux [chaîne](../cppcx/platform-string-class.md) objets dans un nouveau [chaîne](../cppcx/platform-string-class.md) objet.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String`.

*str2*<br/>
Deuxième objet `String` dont le contenu sera ajouté à `str1`.

### <a name="return-value"></a>Valeur de retour

**true** si *str1* est égal à *str2*; sinon, **false**.

### <a name="remarks"></a>Notes

Cet opérateur crée un objet `String^` qui contient les données des deux opérandes. Utilisez-le pour des raisons pratiques lorsque la performance extrême n'est pas critique. Certains appels à « `+` » dans une fonction ne seront peut-être pas visibles, mais si vous manipulez des objets volumineux ou des données texte dans une boucle serrée, utilisez ensuite les mécanismes et les types C++ standard.

##  <a name="operator-equality"></a> String::operator ==, opérateur

Indique si deux objets String spécifiés ont la même valeur de type texte.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String` à comparer.

*str2*<br/>
Deuxième objet `String` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si le contenu de `str1` sont égaux à `str2`; sinon, **false**.

### <a name="remarks"></a>Notes

Cet opérateur équivaut à [String::CompareOrdinal](#compareordinal).

##  <a name="operator-greater-than"></a>  String::operator&gt;

Indique si la valeur d’un `String` objet est supérieur à la valeur d’un deuxième `String` objet.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String`.

*str2*<br/>
Second objet `String`.

### <a name="return-value"></a>Valeur de retour

**true** si la valeur de `str1` est supérieure à la valeur de `str2`; sinon, **false**.

### <a name="remarks"></a>Notes

Cet opérateur équivaut à appeler explicitement [String::CompareOrdinal](#compareordinal) et obtenir un résultat supérieur à zéro.

## <a name="operator-greater-than-or-equals"></a> String::operator&gt;=

Indique si la valeur d’un `String` objet est supérieure ou égale à la valeur de seconde `String` objet.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String`.

*str2*<br/>
Second objet `String`.

### <a name="return-value"></a>Valeur de retour

**true** si la valeur de `str1` est supérieure ou égale à la valeur de `str2`; sinon, **false**.

## <a name="operator-inequality"></a> String::operator ! =

Indique si deux spécifiée `String` objets ont des valeurs différentes.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String` à comparer.

*str2*<br/>
Deuxième objet `String` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si `str1` n’est pas égal à `str2`; sinon, **false**.

## <a name="operator-less-than"></a> String::operator&lt;

Indique si la valeur d’un `String` objet est inférieur à la valeur d’un deuxième `String` objet.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String`.

*str2*<br/>
Second objet `String`.

### <a name="return-value"></a>Valeur de retour

**true** si la valeur de *str1* est inférieure à la valeur de *str2*; sinon, **false**.

## <a name="ctor"></a> String::String, constructeur

Initialise une nouvelle instance de la `String` classe avec une copie de la chaîne d’entrée.

### <a name="syntax"></a>Syntaxe

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Paramètres

*s*<br/>
Ensemble de caractères larges qui initialisent la chaîne. char16

*n*<br/>
Nombre qui spécifie la longueur de la chaîne.

### <a name="remarks"></a>Notes

Si les performances sont importantes et que vous contrôlez la durée de vie de la chaîne source, vous pouvez utiliser [Platform::StringReference](../cppcx/platform-stringreference-class.md) à la place de chaîne.
### <a name="example"></a>Exemple

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a> String::ToString

Retourne un `String` objet dont la valeur est identique à la chaîne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Valeur de retour

Un `String` objet dont la valeur est identique à la chaîne actuelle.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)