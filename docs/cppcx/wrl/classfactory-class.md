---
description: 'En savoir plus sur : classe ClassFactory'
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
ms.openlocfilehash: e6503cba1060c432b2cb85020799b83f0ee16c6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135302"
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
Interface avant toute chose.

*I1*<br/>
Première interface.

*I2*<br/>
Deuxième interface.

## <a name="remarks"></a>Notes

Utilisez `ClassFactory` pour fournir une implémentation de fabrique définie par l’utilisateur.

Le modèle de programmation suivant montre comment utiliser la structure [Implements](implements-structure.md) pour spécifier plus de trois interfaces sur une fabrique de classe.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                        | Description
------------------------------------------- | -----------
[ClassFactory :: ClassFactory](#classfactory) |

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                            | Description
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory :: AddRef](#addref)                 | Incrémente le décompte de références pour l' `ClassFactory` objet actuel.
[ClassFactory :: LockServer,](#lockserver)         | Incrémente ou décrémente le nombre d’objets sous-jacents qui sont suivis par l' `ClassFactory` objet actuel.
[ClassFactory :: QueryInterface](#queryinterface) | Récupère un pointeur vers l’interface spécifiée par le paramètre.
[ClassFactory :: Release](#release)               | Décrémente le décompte de références pour l' `ClassFactory` objet actuel.

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

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a> ClassFactory :: AddRef

Incrémente le décompte de références pour l' `ClassFactory` objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a> ClassFactory :: ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a> ClassFactory :: LockServer,

Incrémente ou décrémente le nombre d’objets sous-jacents qui sont suivis par l' `ClassFactory` objet actuel.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
**`true`** pour incrémenter le nombre d’objets suivis. **`false`** pour décrémenter le nombre d’objets suivis.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, E_FAIL.

### <a name="remarks"></a>Notes

`ClassFactory` effectue le suivi des objets dans une instance sous-jacente de la classe de [module](module-class.md) .

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a> ClassFactory :: QueryInterface

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
Lorsque cette opération est terminée, il s’agit d’un pointeur vers l’interface spécifiée par le paramètre *riid*.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="classfactoryrelease"></a><a name="release"></a> ClassFactory :: Release

Décrémente le décompte de références pour l' `ClassFactory` objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.
