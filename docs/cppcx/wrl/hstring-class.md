---
description: 'En savoir plus sur : classe HString'
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
ms.openlocfilehash: 3a7de2595fbc55cec21f74193cc53f29438530cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229156"
---
# <a name="hstring-class"></a>HString, classe

Classe d’assistance pour la gestion de la durée de vie d’un [HSTRING](/windows/win32/WinRT/hstring) à l’aide du modèle RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Notes

Le Windows Runtime permet d’accéder aux chaînes via des handles [HSTRING](/windows/win32/WinRT/hstring) . La `HString` classe fournit des fonctions et des opérateurs pratiques pour simplifier l’utilisation des handles HSTRING. Cette classe peut gérer la durée de vie du HSTRING qu’elle possède via un modèle RAII.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                | Description
----------------------------------- | -----------------------------------------------------
[HString :: HString](#hstring)        | Initialise une nouvelle instance de la classe `HString`.
[HString :: ~ HString](#tilde-hstring) | Détruit l’instance actuelle de la `HString` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                     | Description
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString :: Attach](#attach)               | Associe l' `HString` objet spécifié à l' `HString` objet actuel.
[HString::CopyTo](#copyto)               | Copie l' `HString` objet actuel dans un objet HSTRING.
[HString ::D Etach](#detach)               | Dissocie l’objet spécifié `HString` de sa valeur sous-jacente.
[HString :: obtient](#get)                     | Récupère la valeur du handle HSTRING sous-jacent.
[HString :: Getaddressof,](#getaddressof)   | Récupère un pointeur vers le handle HSTRING sous-jacent.
[HString :: GetRawBuffer](#getrawbuffer)   | Récupère un pointeur vers les données de chaîne sous-jacentes.
[HString :: IsValid](#isvalid)             | Indique si l' `HString` objet actuel est valide.
[HString :: Makereference,](#makereference) | Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifié.
[HString :: Release](#release)             | Supprime la valeur de chaîne sous-jacente et initialise l' `HString` objet actuel à une valeur vide.
[HString :: Set](#set)                     | Affecte la valeur de l' `HString` objet actuel au paramètre ou à la chaîne de caractères larges spécifiés `HString` .

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                         | Description
-------------------------------------------- | ----------------------------------------------------------------------------
[HString :: Operator =](#operator-assign)       | Déplace la valeur d’un autre `HString` objet vers l' `HString` objet actuel.
[HString :: Operator = =](#operator-equality)    | Indique si les deux paramètres sont égaux.
[HString :: Operator ! =](#operator-inequality)  | Indique si les deux paramètres ne sont pas égaux.
[HString ::, opérateur&lt;](#operator-less-than) | Indique si le premier paramètre est inférieur au second paramètre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HString`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="hstringhstring"></a><a name="tilde-hstring"></a> HString :: ~ HString

Détruit l’instance actuelle de la `HString` classe.

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a> HString :: Attach

Associe l' `HString` objet spécifié à l' `HString` objet actuel.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Paramètres

*hstr*<br/>
Objet `HString` existant.

## <a name="hstringcopyto"></a><a name="copyto"></a> HString :: CopyTo

Copie l' `HString` objet actuel dans un objet HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
HSTRING qui reçoit la copie.

### <a name="remarks"></a>Notes

Cette méthode appelle la fonction [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) .

## <a name="hstringdetach"></a><a name="detach"></a> HString ::D Etach

Dissocie l’objet spécifié `HString` de sa valeur sous-jacente.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Valeur renvoyée

Valeur sous-jacente `HString` avant le début de l’opération de détachement.

## <a name="hstringget"></a><a name="get"></a> HString :: obtient

Récupère la valeur du handle HSTRING sous-jacent.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valeur renvoyée

Valeur du handle HSTRING sous-jacent

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a> HString :: Getaddressof,

Récupère un pointeur vers le handle HSTRING sous-jacent.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le handle HSTRING sous-jacent.

### <a name="remarks"></a>Notes

Après cette opération, la valeur de chaîne du descripteur HSTRING sous-jacent est détruite.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a> HString :: GetRawBuffer

Récupère un pointeur vers les données de chaîne sous-jacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Paramètres

*longueur* Pointeur vers une **`int`** variable qui reçoit la longueur des données.

### <a name="return-value"></a>Valeur renvoyée

**`const`** Pointeur vers les données de chaîne sous-jacentes.

## <a name="hstringhstring"></a><a name="hstring"></a> HString :: HString

Initialise une nouvelle instance de la classe `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Paramètres

*hstr*<br/>
Handle HSTRING.

*autres*<br/>
Objet `HString` existant.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un nouvel `HString` objet qui est vide.

Le deuxième constructeur initialise un nouvel `HString` objet à la valeur de l' *autre* paramètre existant, puis détruit l' *autre* paramètre.

## <a name="hstringisvalid"></a><a name="isvalid"></a> HString :: IsValid

Indique si l' `HString` objet actuel est vide ou non.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Paramètres

**`true`** Si l' `HString` objet actuel n’est pas vide ; sinon, **`false`** .

## <a name="hstringmakereference"></a><a name="makereference"></a> HString :: Makereference,

Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifié.

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

*Taille*<br/>
Paramètre de modèle qui spécifie la taille de la `HStringReference` mémoire tampon de destination.

*str*<br/>
Référence à une chaîne de caractères larges.

*len*<br/>
Longueur maximale de la mémoire tampon de paramètre *Str* à utiliser dans cette opération. Si le paramètre *Len* n’est pas spécifié, le paramètre *Str* entier est utilisé.

### <a name="return-value"></a>Valeur renvoyée

`HStringReference`Objet dont la valeur est identique au paramètre *Str* spécifié.

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a> HString :: Operator =, opérateur

Déplace la valeur d’un autre `HString` objet vers l' `HString` objet actuel.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Objet `HString` existant.

### <a name="remarks"></a>Notes

La valeur de l' *autre* objet existant est copiée dans l' `HString` objet actuel, puis l' *autre* objet est détruit.

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a> HString :: Operator = =, opérateur

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

*LHS*<br/>
Premier paramètre à comparer. *LHS* peut être un `HString` `HStringReference` objet ou, ou un handle HSTRING.

*rhs*<br/>
Deuxième paramètre à comparer. *RHS* peut être un `HString` `HStringReference` objet ou, ou un handle HSTRING.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les paramètres *LHS* et *RHS* sont égaux ; Sinon, **`false`** .

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a> HString :: Operator ! =, opérateur

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

*LHS*<br/>
Premier paramètre à comparer. *LHS* peut être un `HString` `HStringReference` objet ou, ou un handle HSTRING.

*rhs*<br/>
Deuxième paramètre à comparer. *RHS* peut être un `HString` `HStringReference` objet ou, ou un handle HSTRING.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les paramètres *LHS* et *RHS* ne sont pas égaux ; Sinon, **`false`** .

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a> HString :: Operator, &lt; opérateur

Indique si le premier paramètre est inférieur au second paramètre.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier paramètre à comparer. *LHS* peut être une référence à un `HString` .

*rhs*<br/>
Deuxième paramètre à comparer. *RHS* peut être une référence à un `HString` .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le paramètre *LHS* est inférieur au paramètre *RHS* ; Sinon, **`false`** .

## <a name="hstringrelease"></a><a name="release"></a> HString :: Release

Supprime la valeur de chaîne sous-jacente et initialise l' `HString` objet actuel à une valeur vide.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a> HString :: Set

Affecte la valeur de l' `HString` objet actuel au paramètre ou à la chaîne de caractères larges spécifiés `HString` .

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

*str*<br/>
Chaîne de caractères larges.

*len*<br/>
Longueur maximale du paramètre *Str* qui est assignée à l' `HString` objet actuel.

*hstr*<br/>
Objet `HString` existant.
