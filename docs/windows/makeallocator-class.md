---
title: MakeAllocator (classe) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 94c094fe21127592bd8756d0f0b467e2c74df487
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789239"
---
# <a name="makeallocator-class"></a>MakeAllocator (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un nom de type.

*hasWeakReferenceSupport*<br/>
`true` pour allouer de mémoire pour un objet qui prend en charge les références faibles ; `false` d’allocation de mémoire pour un objet qui ne prend pas en charge les références faibles.

## <a name="remarks"></a>Notes

Alloue la mémoire pour une classe activable, avec ou sans prise en charge de la référence faible.

Remplacer la `MakeAllocator` classe pour implémenter un modèle d’allocation de mémoire défini par l’utilisateur.

`MakeAllocator` sert généralement à empêcher les fuites de mémoire si un objet lève pendant la construction.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                  | Description
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Initialise une nouvelle instance de la classe `MakeAllocator`.
[MakeAllocator :: ~ MakeAllocator](#tilde-makeallocator) | Annule l’initialisation de l’instance actuelle de la `MakeAllocator` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                 | Description
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | Alloue de la mémoire et l’associe à actuel `MakeAllocator` objet.
[MakeAllocator::Detach](#detach)     | Dissocie la mémoire allouée par le [Allocate](#allocate) (méthode) à partir du `MakeAllocator` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`MakeAllocator`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="allocate"></a>MakeAllocator::Allocate

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un pointeur vers la mémoire allouée ; Sinon, `nullptr`.

### <a name="remarks"></a>Notes

Alloue de la mémoire et l’associe à actuel `MakeAllocator` objet.

La taille de la mémoire allouée est la taille du type spécifié par l’actuel `MakeAllocator` paramètre de modèle.

Un développeur a besoin remplacer uniquement le `Allocate()` méthode pour implémenter un modèle d’allocation de mémoire différentes.

## <a name="detach"></a>MakeAllocator::Detach

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Notes

Dissocie la mémoire allouée par le [Allocate](#allocate) (méthode) à partir du `MakeAllocator` objet.

Si vous appelez `Detach()`, vous êtes responsable de la suppression de la mémoire fournie par le `Allocate` (méthode).

## <a name="makeallocator"></a>MakeAllocator::MakeAllocator

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `MakeAllocator`.

## <a name="tilde-makeallocator"></a>MakeAllocator :: ~ MakeAllocator

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Notes

Annule l’initialisation de l’instance actuelle de la `MakeAllocator` classe.

Ce destructeur supprime également la mémoire allouée sous-jacent si nécessaire.
