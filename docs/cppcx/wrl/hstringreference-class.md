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
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371423"
---
# <a name="hstringreference-class"></a>HStringReference, classe

Représente un HSTRING qui est créé à partir d’une chaîne existante.

## <a name="syntax"></a>Syntaxe

```cpp
class HStringReference;
```

## <a name="remarks"></a>Notes

La durée de vie du tampon de sauvegarde dans le nouveau HSTRING n’est pas gérée par le Windows Runtime. L’appelant alloue une chaîne source sur le cadre de la pile pour éviter une allocation de tas et pour éliminer le risque d’une fuite de mémoire. En outre, l’appelant doit s’assurer que la chaîne de source reste inchangée pendant la durée de vie du HSTRING attaché. Pour plus d’informations, voir [la fonction WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                    | Description
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Initialise une nouvelle instance de la classe `HStringReference`.

### <a name="public-methods"></a>M&#233;thodes publiques

Membre                              | Description
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Copie de `HStringReference` l’objet actuel à un objet HSTRING.
[HStringReference::Get](#get)       | Récupère la valeur de la poignée HSTRING sous-jacente.
[HStringReference::GetRawBuffer](#getrawbuffer) | Récupère un pointeur sur les données de chaîne sous-jacentes.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                  | Description
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::opérateur](#operator-assign)       | Déplace la valeur `HStringReference` d’un `HStringReference` autre objet à l’objet actuel.
[HStringReference::opérateur](#operator-equality)    | Indique si les deux paramètres sont égaux.
[HStringReference::opérateur!](#operator-inequality)  | Indique si les deux paramètres ne sont pas égaux.
[HStringReference::opérateur&lt;](#operator-less-than) | Indique si le premier paramètre est inférieur au deuxième paramètre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HStringReference`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference::CopyTo

Copie de `HStringReference` l’objet actuel à un objet HSTRING.

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

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference::Get

Récupère la valeur de la poignée HSTRING sous-jacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valeur de retour

La valeur de la poignée sous-jacente HSTRING.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Récupère un pointeur sur les données de chaîne sous-jacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Paramètres

*longueur* Pointeur vers une variable **int** qui reçoit la longueur des données.

### <a name="return-value"></a>Valeur de retour

Un pointeur **const** aux données de chaîne sous-jacentes.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference::HStringReference

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

*tailleDest*<br/>
Un paramètre de modèle qui spécifie la taille du tampon de destination. `HStringReference`

*Str*<br/>
Une référence à une chaîne de caractère large.

*Len*<br/>
La longueur maximale du tampon de paramètre *str* à utiliser dans cette opération. Si le *paramètre len* n’est pas spécifié, l’ensemble du *paramètre str* est utilisé. Si *len* est plus grand que *la tailleDest*, *len* est réglé à *la tailleDest*-1.

*Autres*<br/>
Un `HStringReference` autre objet.

### <a name="remarks"></a>Notes

Le premier constructeur initialise `HStringReference` un nouvel objet de la même taille que le *paramètre str.*

Le deuxième constructeur initialise `HStringReference` un nouvel objet que la taille specifeid par paramètre *len*.

Le troisième constructeur initialise `HStringReference` un nouvel objet à la valeur de *l’autre* paramètre, puis détruit *l’autre* paramètre.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference::opérateur

Déplace la valeur `HStringReference` d’un `HStringReference` autre objet à l’objet actuel.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Objet `HStringReference` existant.

### <a name="remarks"></a>Notes

La valeur de l’autre objet existant `HStringReference` est copiée sur l’objet actuel, puis *l’autre* objet est détruit. *other*

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference::opérateur

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

*Lhs*<br/>
Le premier paramètre à comparer. *lhs* peut `HStringReference` être un objet ou une poignée HSTRING.

*rhs*<br/>
Le deuxième paramètre à comparer.  *rhs* peut `HStringReference` être un objet ou une poignée HSTRING.

### <a name="return-value"></a>Valeur de retour

**vrai** si les paramètres *lhs* et *rhs* sont égaux; autrement, **faux**.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference::opérateur!

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

*Lhs*<br/>
Le premier paramètre à comparer. *lhs* peut `HStringReference` être un objet ou une poignée HSTRING.

*rhs*<br/>
Le deuxième paramètre à comparer.  *rhs* peut `HStringReference` être un objet ou une poignée HSTRING.

### <a name="return-value"></a>Valeur de retour

**vrai** si les paramètres *lhs* et *rhs* ne sont pas égaux; autrement, **faux**.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference::opérateur&lt;

Indique si le premier paramètre est inférieur au deuxième paramètre.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
Le premier paramètre à comparer. *lhs* peut être une `HStringReference`référence à un .

*rhs*<br/>
Le deuxième paramètre à comparer.  *rhs* peut être une `HStringReference`référence à un .

### <a name="return-value"></a>Valeur de retour

**vrai** si le *paramètre lhs* est inférieur au paramètre *rhs;* autrement, **faux**.
