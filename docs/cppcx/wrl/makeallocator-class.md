---
description: 'En savoir plus sur : classe MakeAllocator'
title: MakeAllocator (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: c4e550dec37096a5ff6a41eccd4eb41968721a7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344521"
---
# <a name="makeallocator-class"></a>MakeAllocator (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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
**`true`** pour allouer de la mémoire pour un objet qui prend en charge les références faibles ; **`false`** pour allouer de la mémoire pour un objet qui ne prend pas en charge les références faibles.

## <a name="remarks"></a>Notes

Alloue de la mémoire pour une classe activable, avec ou sans prise en charge de la référence faible.

Substituez la `MakeAllocator` classe pour implémenter un modèle d’allocation de mémoire défini par l’utilisateur.

`MakeAllocator` est généralement utilisé pour empêcher les fuites de mémoire si un objet lève une exception pendant la construction.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                  | Description
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator :: MakeAllocator](#makeallocator)        | Initialise une nouvelle instance de la classe `MakeAllocator`.
[MakeAllocator :: ~ MakeAllocator](#tilde-makeallocator) | Désinitialise l’instance actuelle de la `MakeAllocator` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                 | Description
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator :: Allocate](#allocate) | Alloue de la mémoire et l’associe à l' `MakeAllocator` objet actuel.
[MakeAllocator ::D Etach](#detach)     | Dissocie la mémoire allouée par la méthode [allocate](#allocate) à partir de l' `MakeAllocator` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`MakeAllocator`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="makeallocatorallocate"></a><a name="allocate"></a> MakeAllocator :: Allocate

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, pointeur vers la mémoire allouée ; Sinon, **`nullptr`** .

### <a name="remarks"></a>Notes

Alloue de la mémoire et l’associe à l' `MakeAllocator` objet actuel.

La taille de la mémoire allouée correspond à la taille du type spécifié par le `MakeAllocator` paramètre de modèle actuel.

Un développeur doit remplacer uniquement la `Allocate()` méthode pour implémenter un modèle d’allocation de mémoire différent.

## <a name="makeallocatordetach"></a><a name="detach"></a> MakeAllocator ::D Etach

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Notes

Dissocie la mémoire allouée par la méthode [allocate](#allocate) à partir de l' `MakeAllocator` objet actuel.

Si vous appelez `Detach()` , vous êtes responsable de la suppression de la mémoire fournie par la `Allocate` méthode.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a> MakeAllocator :: MakeAllocator

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `MakeAllocator`.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a> MakeAllocator :: ~ MakeAllocator

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Notes

Désinitialise l’instance actuelle de la `MakeAllocator` classe.

Ce destructeur supprime également la mémoire allouée sous-jacente, si nécessaire.
