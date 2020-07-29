---
title: HStringReference, classe
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: 871696f4a970b1ef9d1f5d36d2e17184b93c9e8b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212980"
---
# <a name="hstringreference-class"></a>HStringReference, classe

Représente un HSTRING créé à partir d’une chaîne existante.

## <a name="syntax"></a>Syntaxe

```cpp
class HStringReference;
```

## <a name="remarks"></a>Notes

La durée de vie de la mémoire tampon de stockage dans le nouvel HSTRING n’est pas gérée par le Windows Runtime. L’appelant alloue une chaîne source sur le frame de pile pour éviter une allocation de tas et éliminer le risque d’une fuite de mémoire. En outre, l’appelant doit s’assurer que la chaîne source reste inchangée pendant la durée de vie du HSTRING attaché. Pour plus d’informations, consultez [fonction WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                    | Description
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference :: HStringReference](#hstringreference) | Initialise une nouvelle instance de la classe `HStringReference`.

### <a name="public-methods"></a>M&#233;thodes publiques

Membre                              | Description
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Copie l' `HStringReference` objet actuel dans un objet HSTRING.
[HStringReference :: obtient](#get)       | Récupère la valeur du handle HSTRING sous-jacent.
[HStringReference :: GetRawBuffer](#getrawbuffer) | Récupère un pointeur vers les données de chaîne sous-jacentes.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                  | Description
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference :: Operator =](#operator-assign)       | Déplace la valeur d’un autre `HStringReference` objet vers l' `HStringReference` objet actuel.
[HStringReference :: Operator = =](#operator-equality)    | Indique si les deux paramètres sont égaux.
[HStringReference :: Operator ! =](#operator-inequality)  | Indique si les deux paramètres ne sont pas égaux.
[HStringReference ::, opérateur&lt;](#operator-less-than) | Indique si le premier paramètre est inférieur au second paramètre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HStringReference`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference :: CopyTo

Copie l' `HStringReference` objet actuel dans un objet HSTRING.

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

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference :: obtient

Récupère la valeur du handle HSTRING sous-jacent.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valeur de retour

Valeur du handle HSTRING sous-jacent.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference :: GetRawBuffer

Récupère un pointeur vers les données de chaîne sous-jacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Paramètres

*longueur* Pointeur vers une **`int`** variable qui reçoit la longueur des données.

### <a name="return-value"></a>Valeur de retour

**`const`** Pointeur vers les données de chaîne sous-jacentes.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference :: HStringReference

Initialise une nouvelle instance de la classe `HStringReference`.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
Paramètre de modèle qui spécifie la taille de la `HStringReference` mémoire tampon de destination.

*str*<br/>
Référence à une chaîne de caractères larges.

*Len*<br/>
Longueur maximale de la mémoire tampon de paramètre *Str* à utiliser dans cette opération. Si le paramètre *Len* n’est pas spécifié, le paramètre *Str* entier est utilisé. Si la fonction *Len* est supérieure à la *taille*la plus grande, *Len* est défini sur la valeur la plus *taille*-1.

*autres*<br/>
Autre `HStringReference` objet.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un nouvel `HStringReference` objet qui a la même taille que le paramètre *Str*.

Le deuxième constructeur initialise un nouvel `HStringReference` objet dont la taille est specifeid par le paramètre *Len*.

Le troisième constructeur initialise un nouvel `HStringReference` objet à la valeur de l' *autre* paramètre, puis détruit l' *autre* paramètre.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference :: Operator =

Déplace la valeur d’un autre `HStringReference` objet vers l' `HStringReference` objet actuel.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Objet `HStringReference` existant.

### <a name="remarks"></a>Notes

La valeur de l' *autre* objet existant est copiée dans l' `HStringReference` objet actuel, puis l' *autre* objet est détruit.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference :: Operator = =

Indique si les deux paramètres sont égaux.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier paramètre à comparer. *LHS* peut être un `HStringReference` objet ou un handle HSTRING.

*rhs*<br/>
Deuxième paramètre à comparer.  *RHS* peut être un `HStringReference` objet ou un handle HSTRING.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les paramètres *LHS* et *RHS* sont égaux ; Sinon, **`false`** .

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference :: Operator ! =

Indique si les deux paramètres ne sont pas égaux.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier paramètre à comparer. *LHS* peut être un `HStringReference` objet ou un handle HSTRING.

*rhs*<br/>
Deuxième paramètre à comparer.  *RHS* peut être un `HStringReference` objet ou un handle HSTRING.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les paramètres *LHS* et *RHS* ne sont pas égaux ; Sinon, **`false`** .

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference ::, opérateur&lt;

Indique si le premier paramètre est inférieur au second paramètre.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier paramètre à comparer. *LHS* peut être une référence à un `HStringReference` .

*rhs*<br/>
Deuxième paramètre à comparer.  *RHS* peut être une référence à un `HStringReference` .

### <a name="return-value"></a>Valeur de retour

**`true`** Si le paramètre *LHS* est inférieur au paramètre *RHS* ; Sinon, **`false`** .
