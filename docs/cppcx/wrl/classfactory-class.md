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
ms.openlocfilehash: 3b738cc8f439e6653162ab99b0a26e87aa8fee36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372667"
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
L’interface zéro.

*I1 (en)*<br/>
La première interface.

*I2 (en)*<br/>
La deuxième interface.

## <a name="remarks"></a>Notes

Utiliser `ClassFactory` pour fournir une mise en œuvre d’usine définie par l’utilisateur.

Le modèle de programmation suivant montre comment utiliser la structure [Implements](implements-structure.md) pour spécifier plus de trois interfaces sur une usine de classe.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                        | Description
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                            | Description
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | Incréments le nombre de `ClassFactory` références pour l’objet actuel.
[ClassFactory::LockServer](#lockserver)         | Incréments ou décroissant le nombre d’objets `ClassFactory` sous-jacents suivis par l’objet actuel.
[ClassFactory::QueryInterface](#queryinterface) | Récupère un pointeur sur l’interface spécifiée par paramètre.
[ClassFactory::Libération](#release)               | Décrément le nombre de `ClassFactory` références pour l’objet actuel.

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

**En-tête:** module.h

**Espace de noms :** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory::AddRef

Incréments le nombre de `ClassFactory` références pour l’objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory::LockServer

Incréments ou décroissant le nombre d’objets `ClassFactory` sous-jacents suivis par l’objet actuel.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
**fidèle** à l’augmentation du nombre d’objets suivis. **faux** pour décroisser le nombre d’objets suivis.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, E_FAIL.

### <a name="remarks"></a>Notes

`ClassFactory`garde une trace des objets dans un cas sous-jacent de la classe [Module.](module-class.md)

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory::QueryInterface

Récupère un pointeur sur l’interface spécifiée par paramètre.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque cette opération se termine, un pointeur à l’interface spécifiée par le *paramètre riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory::Libération

Décrément le nombre de `ClassFactory` références pour l’objet actuel.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.
