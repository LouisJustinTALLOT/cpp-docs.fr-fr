---
title: ClassFactory (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: ccc1c43e8c68053a773883c25704cdea086bd0b1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784276"
---
# <a name="classfactory-class"></a>ClassFactory (classe)

Implémente les fonctionnalités de base de l'interface `IClassFactory`.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Paramètres

*I0*<br/>
L’interface de zéro.

*I1*<br/>
La première interface.

*I2*<br/>
La seconde interface.

## <a name="remarks"></a>Notes

Utiliser `ClassFactory` pour fournir une implémentation de fabrique défini par l’utilisateur.

Le modèle de programmation suivant montre comment utiliser le [implémente](implements-structure.md) structure pour spécifier plus de trois interfaces sur une fabrique de classe.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                        | Description
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                            | Description
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | Incrémente le décompte de références pour actuel `ClassFactory` objet.
[ClassFactory::LockServer](#lockserver)         | Incrémente ou décrémente le nombre de sous-jacent objets qui sont suivis par le `ClassFactory` objet.
[ClassFactory::QueryInterface](#queryinterface) | Récupère un pointeur vers l’interface spécifiée par le paramètre.
[ClassFactory::Release](#release)               | Décrémente le décompte de références pour actuel `ClassFactory` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::wrl

## <a name="addref"></a>ClassFactory::AddRef

Incrémente le décompte de références pour actuel `ClassFactory` objet.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="lockserver"></a>ClassFactory::LockServer

Incrémente ou décrémente le nombre de sous-jacent objets qui sont suivis par le `ClassFactory` objet.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*fLock*<br/>
**true** pour incrémenter le nombre d’objets suivis. **false** pour décrémenter le nombre d’objets suivis.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_FAIL.

### <a name="remarks"></a>Notes

`ClassFactory` effectue le suivi des objets dans une instance sous-jacente de la [Module](module-class.md) classe.

## <a name="queryinterface"></a>ClassFactory::QueryInterface

Récupère un pointeur vers l’interface spécifiée par le paramètre.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque cette opération se termine, un pointeur vers l’interface spécifiée par le paramètre *riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="release"></a>ClassFactory::Release

Décrémente le décompte de références pour actuel `ClassFactory` objet.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.
