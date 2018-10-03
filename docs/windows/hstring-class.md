---
title: HString, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fea4f576e347ca03dda1142b3118bf605bc9f385
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235345"
---
# <a name="hstring-class"></a>HString, classe

Une classe d’assistance pour la gestion de la durée de vie d’une chaîne HSTRING utilisant le modèle RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Notes

Le Runtime Windows fournit l’accès aux chaînes via les handles HSTRING. Le `HString` classe fournit des fonctions de commodité et d’opérateurs pour simplifier l’utilisation des handles HSTRING. Cette classe peut gérer la durée de vie de la fonction HSTRING qu’il détient via un modèle RAII.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                | Description
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Initialise une nouvelle instance de la classe `HString`.
[HString :: ~ HString](#tilde-hstring) | Détruit l’instance actuelle de la `HString` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                     | Description
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Associe les `HString` objet actuelle `HString` objet.
[HString::CopyTo](#copyto)               | Copie en cours `HString` objet dans un objet HSTRING.
[HString::Detach](#detach)               | Dissocie spécifié `HString` objet à partir de sa valeur sous-jacente.
[HString::Get](#get)                     | Récupère la valeur du handle HSTRING sous-jacent.
[HString::GetAddressOf](#getaddressof)   | Récupère un pointeur vers le handle HSTRING sous-jacent.
[HString::IsValid](#isvalid)             | Indique si l’actuel `HString` objet est valide.
[HString::MakeReference](#makereference) | Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifiée.
[HString::Release](#release)             | Supprime la valeur de chaîne sous-jacente et initialise actuel `HString` objet à une valeur vide.
[HString::Set](#set)                     | Définit la valeur de cours `HString` objet à la chaîne de caractères larges spécifiée ou `HString` paramètre.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                         | Description
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator =](#operator-assign)       | Déplace la valeur d’un autre `HString` objet actuel `HString` objet.
[HString::operator ==](#operator-equality)    | Indique si les deux paramètres sont égaux.
[HString::operator ! =](#operator-inequality)  | Indique si les deux paramètres ne sont pas égales.
[HString::operator&lt;](#operator-less-than) | Indique si le premier paramètre est inférieur au second.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HString`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString :: ~ HString

Détruit l’instance actuelle de la `HString` classe.

```cpp
~HString() throw()  
```

## <a name="attach"></a>HString::Attach

Associe les `HString` objet actuelle `HString` objet.

```cpp
void Attach(
       HSTRING hstr
       ) throw()  
```

### <a name="parameters"></a>Paramètres

*HSTR*<br/>
Objet `HString` existant.

## <a name="copyto"></a>HString::CopyTo

Copie en cours `HString` objet dans un objet HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
HSTRING qui reçoit la copie.

### <a name="remarks"></a>Notes

Cette méthode appelle la [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) (fonction).

## <a name="detach"></a>HString::Detach

Dissocie spécifié `HString` objet à partir de sa valeur sous-jacente.

```cpp
HSTRING Detach() throw()  
```

### <a name="return-value"></a>Valeur de retour

Sous-jacent `HString` valeur avant de démarrer l’opération de détachement.

## <a name="get"></a>HString::Get

Récupère la valeur du handle HSTRING sous-jacent.

```cpp
HSTRING Get() const throw()  
```

### <a name="return-value"></a>Valeur de retour

La valeur du handle HSTRING sous-jacent

## <a name="getaddressof"></a>HString::GetAddressOf

Récupère un pointeur vers le handle HSTRING sous-jacent.

```cpp
HSTRING* GetAddressOf() throw()  
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le handle HSTRING sous-jacent.

### <a name="remarks"></a>Notes

Après cette opération, la valeur de chaîne du handle HSTRING sous-jacent est détruite.

## <a name="hstring"></a>HString::HString

Initialise une nouvelle instance de la classe `HString`.

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Paramètres

*HSTR*<br/>
Un handle HSTRING.

*other*<br/>
Objet `HString` existant.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un nouveau `HString` objet est vide.

Le deuxième constructeur initialise un nouveau `HString` objet à la valeur existants *autres* paramètre et détruit le *autres* paramètre.

## <a name="isvalid"></a>HString::IsValid

Indique si l’actuel `HString` objet est vide ou non.

```cpp
bool IsValid() const throw()  
```

### <a name="parameters"></a>Paramètres

`true` Si actuel `HString` objet n’est pas vide ; sinon, `false`.

## <a name="makereference"></a>HString::MakeReference

Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifiée.

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

*sizeDest*<br/>
Un paramètre de modèle qui spécifie la taille de la destination `HStringReference` mémoire tampon.

*str*<br/>
Une référence à une chaîne à caractères larges.

*Len*<br/>
La longueur maximale de la *str* mémoire tampon de paramètre à utiliser dans cette opération. Si le *len* paramètre n’est pas spécifié, l’intégralité de *str* paramètre est utilisé.

### <a name="return-value"></a>Valeur de retour

Un `HStringReference` objet dont la valeur est identique à celui du texte spécifié *str* paramètre.

## <a name="operator-assign"></a>HString::operator =, opérateur

Déplace la valeur d’un autre `HString` objet actuel `HString` objet.

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Objet `HString` existant.

### <a name="remarks"></a>Notes

La valeur existants *autres* objet est copié dans le cours `HString` objet, puis le *autres* détruit.

## <a name="operator-equality"></a>HString::operator ==, opérateur

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
Le premier paramètre à comparer. *LHS* peut être un `HString` ou `HStringReference` objet ou un handle HSTRING.

*terme de droite*<br/>
Le deuxième paramètre à comparer. *rhs* peut être un `HString` ou `HStringReference` objet ou un handle HSTRING.

### <a name="return-value"></a>Valeur de retour

`true` Si le *lhs* et *rhs* paramètres sont égaux ; sinon, `false`.

## <a name="operator-inequality"></a>HString::operator ! =, opérateur

Indique si les deux paramètres ne sont pas égales.

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
Le premier paramètre à comparer. *LHS* peut être un `HString` ou `HStringReference` objet ou un handle HSTRING.

*terme de droite*<br/>
Le deuxième paramètre à comparer. *rhs* peut être un `HString` ou `HStringReference` objet ou un handle HSTRING.

### <a name="return-value"></a>Valeur de retour

`true` Si le *lhs* et *rhs* paramètres ne sont pas égales ; sinon, `false`.

## <a name="operator-less-than"></a>HString::operator&lt; opérateur

Indique si le premier paramètre est inférieur au second.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()  
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Le premier paramètre à comparer. *LHS* peut être une référence à un `HString`.

*terme de droite*<br/>
Le deuxième paramètre à comparer. *RHS* peut être une référence à un `HString`.

### <a name="return-value"></a>Valeur de retour

`true` Si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, `false`.

## <a name="release"></a>HString::Release

Supprime la valeur de chaîne sous-jacente et initialise actuel `HString` objet à une valeur vide.

```cpp
void Release() throw()  
```

## <a name="set"></a>HString::Set

Définit la valeur de cours `HString` objet à la chaîne de caractères larges spécifiée ou `HString` paramètre.

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
Une chaîne à caractères larges.

*Len*<br/>
La longueur maximale de la *str* paramètre qui est affectée à l’actuel `HString` objet.

*HSTR*<br/>
Objet `HString` existant.
