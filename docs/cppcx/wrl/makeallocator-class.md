---
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
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371336"
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
**fidèle** à allouer la mémoire pour un objet qui prend en charge les références faibles; **faux** d’allouer la mémoire pour un objet qui ne prend pas en charge les références faibles.

## <a name="remarks"></a>Notes

Alloue la mémoire pour une classe activatable, avec ou sans faible support de référence.

Remplacer la `MakeAllocator` classe pour implémenter un modèle d’allocation de mémoire défini par l’utilisateur.

`MakeAllocator`est généralement utilisé pour prévenir les fuites de mémoire si un objet jette pendant la construction.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                  | Description
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Initialise une nouvelle instance de la classe `MakeAllocator`.
[MakeAllocator::MakeAllocator](#tilde-makeallocator) | Désinitialise l’instance actuelle `MakeAllocator` de la classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                 | Description
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | Alloue la mémoire et `MakeAllocator` l’associe à l’objet actuel.
[MakeAllocator::Detach](#detach)     | Dissocie la mémoire attribuée par la `MakeAllocator` méthode [Allocate](#allocate) de l’objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`MakeAllocator`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator::Allocate

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, un pointeur à la mémoire allouée; autrement, `nullptr`.

### <a name="remarks"></a>Notes

Alloue la mémoire et `MakeAllocator` l’associe à l’objet actuel.

La taille de la mémoire allouée est la `MakeAllocator` taille du type spécifié par le paramètre du modèle actuel.

Un développeur doit passer `Allocate()` outre uniquement la méthode pour implémenter un modèle d’allocation de mémoire différent.

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator::Detach

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Notes

Dissocie la mémoire attribuée par la `MakeAllocator` méthode [Allocate](#allocate) de l’objet actuel.

Si vous `Detach()`appelez, vous êtes responsable de la `Allocate` suppression de la mémoire fournie par la méthode.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator::MakeAllocator

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `MakeAllocator`.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator::MakeAllocator

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Notes

Désinitialise l’instance actuelle `MakeAllocator` de la classe.

Ce destructeur supprime également la mémoire sous-jacente allouée si nécessaire.
