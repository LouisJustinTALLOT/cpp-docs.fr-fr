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
ms.openlocfilehash: 9c17a9df8fcc7d849bbbd4f613bf5dce6dae8983
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894390"
---
# <a name="hstringreference-class"></a>HStringReference, classe

Représente un HSTRING créé à partir d’une chaîne existante.

## <a name="syntax"></a>Syntaxe

```cpp
class HStringReference;
```

## <a name="remarks"></a>Notes

La durée de vie de la mémoire tampon de stockage dans le nouveau HSTRING n’est pas gérée par le Runtime de Windows. L’appelant alloue une chaîne source sur le frame de pile pour éviter une allocation de tas et d’éliminer le risque d’une fuite de mémoire. En outre, l’appelant doit s’assurer que la chaîne source reste inchangée pendant la durée de vie du HSTRING attaché. Pour plus d’informations, consultez [WindowsCreateStringReference fonction](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                    | Description
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Initialise une nouvelle instance de la classe `HStringReference`.

### <a name="public-methods"></a>M&#233;thodes publiques

Membre                              | Description
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Copie en cours `HStringReference` objet dans un objet HSTRING.
[HStringReference::Get](#get)       | Récupère la valeur du handle HSTRING sous-jacent.
[HStringReference::GetRawBuffer](#getrawbuffer) | Récupère un pointeur vers les données de chaîne sous-jacentes.

### <a name="public-operators"></a>Op&#233;rateurs publics

Name                                                  | Description
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | Déplace la valeur d’un autre `HStringReference` objet actuel `HStringReference` objet.
[HStringReference::operator==](#operator-equality)    | Indique si les deux paramètres sont égaux.
[HStringReference::operator!=](#operator-inequality)  | Indique si les deux paramètres ne sont pas égales.
[HStringReference::operator&lt;](#operator-less-than) | Indique si le premier paramètre est inférieur au second.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HStringReference`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="copyto"></a>HStringReference::CopyTo

Copie en cours `HStringReference` objet dans un objet HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
HSTRING qui reçoit la copie.

### <a name="remarks"></a>Notes

Cette méthode appelle la [WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring) (fonction).

## <a name="get"></a>HStringReference::Get

Récupère la valeur du handle HSTRING sous-jacent.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valeur de retour

La valeur du handle HSTRING sous-jacent.

## <a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Récupère un pointeur vers les données de chaîne sous-jacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Paramètres

*longueur* pointeur vers un **int** variable qui reçoit la longueur des données.

### <a name="return-value"></a>Valeur de retour

Un **const** pointeur vers les données de chaîne sous-jacentes.

## <a name="hstringreference"></a>HStringReference::HStringReference

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

*sizeDest*<br/>
Un paramètre de modèle qui spécifie la taille de la destination `HStringReference` mémoire tampon.

*str*<br/>
Une référence à une chaîne à caractères larges.

*len*<br/>
La longueur maximale de la *str* mémoire tampon de paramètre à utiliser dans cette opération. Si le *len* paramètre n’est pas spécifié, l’intégralité de *str* paramètre est utilisé. Si *len* est supérieur à *sizeDest*, *len* a la valeur *sizeDest*-1.

*other*<br/>
Un autre `HStringReference` objet.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un nouveau `HStringReference` objet la même taille que le paramètre *str*.

Le deuxième constructeur initialise un nouveau `HStringReference` de l’objet qui le specifeid de taille par paramètre *len*.

Le troisième constructeur initialise un nouveau `HStringReference` objet à la valeur de la *autres* paramètre et détruit le *autres* paramètre.

## <a name="operator-assign"></a>HStringReference::operator=

Déplace la valeur d’un autre `HStringReference` objet actuel `HStringReference` objet.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Objet `HStringReference` existant.

### <a name="remarks"></a>Notes

La valeur existants *autres* objet est copié dans le cours `HStringReference` objet, puis le *autres* détruit.

## <a name="operator-equality"></a>HStringReference::operator==

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

*lhs*<br/>
Le premier paramètre à comparer. *LHS* peut être un `HStringReference` objet ou un handle HSTRING.

*rhs*<br/>
Le deuxième paramètre à comparer.  *RHS* peut être un `HStringReference` objet ou un handle HSTRING.

### <a name="return-value"></a>Valeur de retour

**true** si le *lhs* et *rhs* paramètres sont égaux ; sinon, **false**.

## <a name="operator-inequality"></a>HStringReference::operator!=

Indique si les deux paramètres ne sont pas égales.

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

*lhs*<br/>
Le premier paramètre à comparer. *LHS* peut être un `HStringReference` objet ou un handle HSTRING.

*rhs*<br/>
Le deuxième paramètre à comparer.  *RHS* peut être un `HStringReference` objet ou un handle HSTRING.

### <a name="return-value"></a>Valeur de retour

**true** si le *lhs* et *rhs* paramètres ne sont pas égales ; sinon, **false**.

## <a name="operator-less-than"></a>HStringReference::operator&lt;

Indique si le premier paramètre est inférieur au second.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le premier paramètre à comparer. *LHS* peut être une référence à un `HStringReference`.

*rhs*<br/>
Le deuxième paramètre à comparer.  *RHS* peut être une référence à un `HStringReference`.

### <a name="return-value"></a>Valeur de retour

**true** si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, **false**.
