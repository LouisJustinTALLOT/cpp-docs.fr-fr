---
title: HString, classe
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371428"
---
# <a name="hstring-class"></a>HString, classe

Une classe d’aide pour gérer la durée de vie d’un [HSTRING](/windows/win32/WinRT/hstring) en utilisant le modèle RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Notes

Le Windows Runtime donne accès aux chaînes via des poignées [HSTRING.](/windows/win32/WinRT/hstring) La `HString` classe fournit des fonctions de commodité et des opérateurs pour simplifier l’utilisation des poignées HSTRING. Cette classe peut gérer la durée de vie du HSTRING qu’il possède grâce à un modèle RAII.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                | Description
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Initialise une nouvelle instance de la classe `HString`.
[HString: : HString](#tilde-hstring) | Détruit l’instance actuelle `HString` de la classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                     | Description
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Associe l’objet `HString` spécifié `HString` à l’objet actuel.
[HString::CopyTo](#copyto)               | Copie de `HString` l’objet actuel à un objet HSTRING.
[HString::Detach](#detach)               | Dissocie l’objet spécifié `HString` de sa valeur sous-jacente.
[HString::Get](#get)                     | Récupère la valeur de la poignée HSTRING sous-jacente.
[HString::GetAddressOf](#getaddressof)   | Récupère un pointeur sur la poignée HSTRING sous-jacente.
[HString::GetRawBuffer](#getrawbuffer)   | Récupère un pointeur sur les données de chaîne sous-jacentes.
[HString::IsValid](#isvalid)             | Indique si `HString` l’objet actuel est valide.
[HString::MakeReference](#makereference) | Crée `HStringReference` un objet à partir d’un paramètre de chaîne spécifié.
[HString::Libération](#release)             | Supprime la valeur de la chaîne sous-jacente et intialise l’objet actuel `HString` à une valeur vide.
[HString::Set](#set)                     | Définit la valeur `HString` de l’objet actuel à `HString` la chaîne ou au paramètre de caractère large spécifié.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                         | Description
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::opérateur](#operator-assign)       | Déplace la valeur `HString` d’un `HString` autre objet à l’objet actuel.
[HString::opérateur](#operator-equality)    | Indique si les deux paramètres sont égaux.
[HString::opérateur!](#operator-inequality)  | Indique si les deux paramètres ne sont pas égaux.
[HString::opérateur&lt;](#operator-less-than) | Indique si le premier paramètre est inférieur au deuxième paramètre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HString`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString: : HString

Détruit l’instance actuelle `HString` de la classe.

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString::Attach

Associe l’objet `HString` spécifié `HString` à l’objet actuel.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Paramètres

*hstr*<br/>
Objet `HString` existant.

## <a name="hstringcopyto"></a><a name="copyto"></a>HString::CopyTo

Copie de `HString` l’objet actuel à un objet HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Le HSTRING qui reçoit la copie.

### <a name="remarks"></a>Notes

Cette méthode appelle la fonction [WindowsDuplicateString.](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)

## <a name="hstringdetach"></a><a name="detach"></a>HString::Detach

Dissocie l’objet spécifié `HString` de sa valeur sous-jacente.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Valeur de retour

La `HString` valeur sous-jacente avant le début de l’opération de détachement.

## <a name="hstringget"></a><a name="get"></a>HString::Get

Récupère la valeur de la poignée HSTRING sous-jacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valeur de retour

La valeur de la poignée sous-jacente HSTRING

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString::GetAddressOf

Récupère un pointeur sur la poignée HSTRING sous-jacente.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la poignée sous-jacente HSTRING.

### <a name="remarks"></a>Notes

Après cette opération, la valeur de chaîne de la poignée sous-jacente HSTRING est détruite.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString::GetRawBuffer

Récupère un pointeur sur les données de chaîne sous-jacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Paramètres

*longueur* Pointeur vers une variable **int** qui reçoit la longueur des données.

### <a name="return-value"></a>Valeur de retour

Un pointeur **const** aux données de chaîne sous-jacentes.

## <a name="hstringhstring"></a><a name="hstring"></a>HString::HString

Initialise une nouvelle instance de la classe `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Paramètres

*hstr*<br/>
Une poignée HSTRING.

*Autres*<br/>
Objet `HString` existant.

### <a name="remarks"></a>Notes

Le premier constructeur initialise `HString` un nouvel objet vide.

Le deuxième constructeur initialise `HString` un nouvel objet à la valeur de *l’autre* paramètre existant, puis détruit *l’autre* paramètre.

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString::IsValid

Indique si `HString` l’objet actuel est vide ou non.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Paramètres

**vrai** si `HString` l’objet actuel n’est pas vide; autrement, **faux**.

## <a name="hstringmakereference"></a><a name="makereference"></a>HString::MakeReference

Crée `HStringReference` un objet à partir d’un paramètre de chaîne spécifié.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Paramètres

*tailleDest*<br/>
Un paramètre de modèle qui spécifie la taille du tampon de destination. `HStringReference`

*Str*<br/>
Une référence à une chaîne de caractère large.

*Len*<br/>
La longueur maximale du tampon de paramètre *str* à utiliser dans cette opération. Si le *paramètre len* n’est pas spécifié, l’ensemble du *paramètre str* est utilisé.

### <a name="return-value"></a>Valeur de retour

Un `HStringReference` objet dont la valeur est la même que le *paramètre str* spécifié.

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString::opérateur opérateur

Déplace la valeur `HString` d’un `HString` autre objet à l’objet actuel.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Objet `HString` existant.

### <a name="remarks"></a>Notes

La valeur de l’autre objet existant `HString` est copiée sur l’objet actuel, puis *l’autre* objet est détruit. *other*

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString::opérateur OPÉRATEUR

Indique si les deux paramètres sont égaux.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le premier paramètre à comparer. *lhs* peut `HString` être `HStringReference` un ou un objet, ou une poignée HSTRING.

*rhs*<br/>
Le deuxième paramètre à comparer. *rhs* peut `HString` être `HStringReference` un ou un objet, ou une poignée HSTRING.

### <a name="return-value"></a>Valeur de retour

**vrai** si les paramètres *lhs* et *rhs* sont égaux; autrement, **faux**.

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString::opérateur!

Indique si les deux paramètres ne sont pas égaux.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le premier paramètre à comparer. *lhs* peut `HString` être `HStringReference` un ou un objet, ou une poignée HSTRING.

*rhs*<br/>
Le deuxième paramètre à comparer. *rhs* peut `HString` être `HStringReference` un ou un objet, ou une poignée HSTRING.

### <a name="return-value"></a>Valeur de retour

**vrai** si les paramètres *lhs* et *rhs* ne sont pas égaux; autrement, **faux**.

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString::opérateur&lt; opérateur

Indique si le premier paramètre est inférieur au deuxième paramètre.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le premier paramètre à comparer. *lhs* peut être une `HString`référence à un .

*rhs*<br/>
Le deuxième paramètre à comparer. *rhs* peut être une `HString`référence à un .

### <a name="return-value"></a>Valeur de retour

**vrai** si le *paramètre lhs* est inférieur au paramètre *rhs;* autrement, **faux**.

## <a name="hstringrelease"></a><a name="release"></a>HString::Libération

Supprime la valeur de la chaîne sous-jacente et intialise l’objet actuel `HString` à une valeur vide.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString::Set

Définit la valeur `HString` de l’objet actuel à `HString` la chaîne ou au paramètre de caractère large spécifié.

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Une corde à caractère large.

*Len*<br/>
La longueur maximale du paramètre *str* `HString` qui est attribué à l’objet actuel.

*hstr*<br/>
Objet `HString` existant.
