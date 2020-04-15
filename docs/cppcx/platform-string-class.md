---
title: Platform::String, classe
ms.date: 10/16/2019
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
ms.openlocfilehash: 3f29c60d0d6a4618d97d8f750a048fcc18f976b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322115"
---
# <a name="platformstring-class"></a>Platform::String, classe

Représente une collection séquentielle de caractères Unicode utilisée pour représenter du texte. Pour plus d’informations et [d’exemples,](../cppcx/strings-c-cx.md)voir Cordes .

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

## <a name="members"></a>Membres

La classe String hérite de la classe Object et des interfaces IDisposable, IEquatable et IPrintable.

La classe String a également les types de membres ci-dessous.

### <a name="constructors"></a>Constructeurs

|Membre|Description|
|------------|-----------------|
|[Chaîne::String](#ctor)|Initialise une nouvelle instance de la classe String.|

### <a name="methods"></a>Méthodes

La classe String hérite des méthodes Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() et ToString() de la [Platform::Object Class](../cppcx/platform-object-class.md). La classe String contient également les méthodes ci-dessous.

|Méthode|Description|
|------------|-----------------|
|[Chaîne::Begin](#begin)|Retourne un pointeur au début de la chaîne actuelle.|
|[Chaîne::CompareOrdinal](#compareordinal)|Compare deux objets `String` en évaluant les valeurs numériques des caractères correspondants dans les deux valeurs de chaîne représentées par les objets.|
|[Chaîne::Concat](#concat)|Concatène les valeurs de deux objets String.|
|[Chaîne::Data](#data)|Retourne un pointeur au début de la chaîne actuelle.|
|[Chaîne::Dispose](#dispose)|Libère des ressources.|
|[Chaîne::Fin](#end)|Retourne un pointeur après la fin de la chaîne actuelle.|
|[Chaîne::Equals](#equals)|Indique si l'objet spécifié est égal à l'objet actif.|
|[Chaîne::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|
|[Chaîne::IsEmpty](#isempty)|Indique si l'objet String actuel est vide.|
|[Chaîne::IsFastPass](#isfastpass)|Indique si l’objet String actuel participe à une opération *de passage rapide.* Dans une opération de passage rapide, le comptage des références est interrompu.|
|[Chaîne::Longueur](#length)|Récupère la longueur de l'objet String en cours.|
|[Chaîne::ToString](#tostring)|Retourne un objet String dont la valeur est identique à celle de la chaîne en cours.|

### <a name="operators"></a>Opérateurs

La classe String a les opérateurs suivants.

|Membre|Description|
|------------|-----------------|
|[Chaîne :opérateurMD Opérateur](#operator-equality)|Indique si deux objets String spécifiés ont la même valeur.|
|[Opérateur opérateur+](#operator-plus)|Concatène deux objets String en un nouvel objet String.|
|[Chaîne::opérateur> opérateur](#operator-greater-than)|Indique si la valeur d'un objet String est supérieure à la valeur d'un deuxième objet String.|
|[Chaîne::opérateur>'Opérateur'](#operator-greater-than-or-equals)|Indique si la valeur d'un objet String est supérieure ou égale à la valeur d'un deuxième objet String.|
|[Chaîne::opérateur!](#operator-inequality)|Indique si deux objets String spécifiés ont des valeurs différentes.|
|[Chaîne::opérateur< opérateur](#operator-less-than)|Indique si la valeur d'un objet String est inférieure à la valeur d'un deuxième objet String.|

### <a name="requirements"></a>Spécifications

**Client pris en charge au minimum :** Windows 8

**Serveur pris en charge minimum :** Serveur Windows 2012

**Espace de noms :** Platform

**En-tête** vccorlib.h (inclus par défaut)

## <a name="stringbegin-method"></a><a name="begin"></a>Chaîne::Méthode De départ

Retourne un pointeur au début de la chaîne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
char16* Begin();
```

### <a name="return-value"></a>Valeur de retour

Pointeur au début de la chaîne actuelle.

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>Chaîne::CompareOrdinal Method

Méthode statique qui `String` compare deux objets en évaluant les valeurs numériques des caractères correspondants dans les deux valeurs de chaîne représentées par les objets.

### <a name="syntax"></a>Syntaxe

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
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

## <a name="stringconcat-method"></a><a name="concat"></a>Chaîne::Méthode Concat

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

## <a name="stringdata-method"></a><a name="data"></a>String::Data Méthode

Retourne un pointeur vers le début de la mémoire tampon de données de l'objet en tant que tableau de style C d'éléments `char16` (`wchar_t`).

### <a name="syntax"></a>Syntaxe

```cpp
const char16* Data();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur au `const char16` début d’un`char16` tableau de caractères `wchar_t`Unicode (est un tapdef pour ).

### <a name="remarks"></a>Notes

Utilisez cette méthode pour convertir de `Platform::String^` en `wchar_t*`. Lorsque l'objet `String` se trouve hors de portée, la validité du pointeur donnée n'est plus garantie. Pour stocker les données au-delà de la durée de vie de l’objet d’origine, `String` utilisez [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) pour copier le tableau dans la mémoire que vous vous êtes alloué.

## <a name="stringdispose-method"></a><a name="dispose"></a>Corde::Dispose Méthode

Libère des ressources.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>Chaîne::Méthode de fin

Retourne un pointeur après la fin de la chaîne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
char16* End();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers au-delà de la fin de la chaîne actuelle.

### <a name="remarks"></a>Notes

Fin() retourne Begin() et Longueur.

## <a name="stringequals-method"></a><a name="equals"></a>Chaîne::Méthode égale

Indique si la chaîne spécifiée a la même valeur que l'objet actif.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** `str` si est égal à l’objet actuel; autrement, **faux**.

### <a name="remarks"></a>Notes

Cette méthode est équivalente à la [chaîne statique::CompareOrdinal](#compareordinal). Dans la première surcharge, il est attendu que le paramètre `str` puisse être casté en un objet String^.

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>Chaîne::GetHashCode Méthode

Retourne le code de hachage de cette instance.

### <a name="syntax"></a>Syntaxe

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Valeur de retour

Code de hachage de cette instance.

## <a name="stringisempty-method"></a><a name="isempty"></a>Chaîne::IsEmpty Méthode

Indique si l'objet String actuel est vide.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Valeur de retour

**vrai** si `String` l’objet actuel est **nul** ou la corde vide (L"); autrement, **faux**.

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>Chaîne::IsFastPass Méthode

Indique si l’objet String actuel participe à une opération *de passage rapide.* Dans une opération de passage rapide, le comptage des références est interrompu.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Valeur de retour

**vrai** si `String` l’objet actuel est rapide-passé; autrement, **faux**.

### <a name="remarks"></a>Notes

Au cours d'un appel de fonction où un objet, dont les références sont comptabilisées, constitue un paramètre, et que la fonction appelée ne lit que cet objet, le compilateur peut sans risque interrompre le décompte de références et améliorer les performances d'appel. Votre code ne peut rien faire d'utile avec cette propriété. Le système gère tous les détails.

## <a name="stringlength-method"></a><a name="length"></a>Chaîne::Méthode de longueur

Récupère le nombre de caractères dans l’objet actuel. `String`

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères dans l’objet actuel. `String`

### <a name="remarks"></a>Notes

La longueur d'une chaîne sans caractères est zéro. La longueur de la chaîne suivante est 5 :

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Le tableau de caractères retourné par le [String::Data](#data) a un caractère supplémentaire, qui est le NULL de fin ou '0'. La longueur de ce caractère est également de deux octets.

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>Chaîne ::opérateur OPÉRATEUR

Concatenates deux objets [à cordes](../cppcx/platform-string-class.md) dans un nouvel objet [String.](../cppcx/platform-string-class.md)

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

**vrai** si *str1* est égal à *str2;* autrement, **faux**.

### <a name="remarks"></a>Notes

Cet opérateur crée un objet `String^` qui contient les données des deux opérandes. Utilisez-le pour des raisons pratiques lorsque la performance extrême n'est pas critique. Certains appels à « `+` » dans une fonction ne seront peut-être pas visibles, mais si vous manipulez des objets volumineux ou des données texte dans une boucle serrée, utilisez ensuite les mécanismes et les types C++ standard.

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>Chaîne :opérateurMD Opérateur

Indique si deux objets String spécifiés ont la même valeur de type texte.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String` à comparer.

*str2*<br/>
Deuxième `String` objet à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** si le `str1` contenu `str2`est égal à ; autrement, **faux**.

### <a name="remarks"></a>Notes

Cet opérateur est équivalent à [String::CompareOrdinal](#compareordinal).

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>Chaîne::opérateur&gt;

Indique si la `String` valeur d’un objet est `String` supérieure à la valeur d’un deuxième objet.

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

**vrai** si la `str1` valeur est supérieure `str2`à la valeur de ; autrement, **faux**.

### <a name="remarks"></a>Notes

Cet opérateur est équivalent à appeler explicitement [String::CompareOrdinal](#compareordinal) et obtenir un résultat supérieur à zéro.

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>Chaîne::opérateur&gt;=

Indique si la `String` valeur d’un objet est supérieure `String` ou égale à la valeur d’un deuxième objet.

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

**vrai** si la `str1` valeur est supérieure ou `str2`égale à la valeur de ; autrement, **faux**.

## <a name="stringoperator"></a><a name="operator-inequality"></a>Chaîne::opérateur!

Indique si `String` deux objets spécifiés ont des valeurs différentes.

### <a name="syntax"></a>Syntaxe

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier objet `String` à comparer.

*str2*<br/>
Deuxième `String` objet à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** `str1` si n’est pas égal à `str2`; autrement, **faux**.

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>Chaîne::opérateur&lt;

Indique si la `String` valeur d’un objet est `String` inférieure à la valeur d’un deuxième objet.

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

**vrai** si la valeur de *str1* est inférieure à la valeur de *str2;* autrement, **faux**.

## <a name="stringstring-constructor"></a><a name="ctor"></a>Chaîne::String Constructor

Initialise une nouvelle instance `String` de la classe avec une copie des données de la chaîne d’entrée.

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

Si les performances sont critiques et que vous contrôlez la durée de vie de la chaîne source, vous pouvez utiliser [Platform::StringReference](../cppcx/platform-stringreference-class.md) à la place de string.

### <a name="example"></a>Exemple

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>Chaîne::ToString

Retourne `String` un objet dont la valeur est la même que la chaîne actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Valeur de retour

Un `String` objet dont la valeur est la même que la chaîne actuelle.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
