---
title: RoInitializeWrapper, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: b43d5bb2f553d298584ab2ae497c22637d3beb0d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784233"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper, classe

Initialise le Runtime de Windows.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Notes

`RoInitializeWrapper` est un pratique qui initialise le Runtime Windows et retourne un HRESULT qui indique si l’opération a réussi. Étant donné que le destructeur de classe appelle `::Windows::Foundation::Uninitialize`, instances de `RoInitializeWrapper` doit être déclarée au niveau de portée globale ou de niveau supérieur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                    | Description
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Initialise une nouvelle instance de la classe `RoInitializeWrapper`.
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | Détruit l’instance actuelle de la `RoInitializeWrapper` classe.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                       | Description
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Récupère la valeur HRESULT produit par le `RoInitializeWrapper` constructeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RoInitializeWrapper`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="hresult"></a>RoInitializeWrapper::HRESULT()

Récupère la valeur HRESULT produite par la dernière `RoInitializeWrapper` constructeur.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Initialise une nouvelle instance de la classe `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
Une des énumérations RO_INIT_TYPE, qui spécifie la prise en charge fournie par le Runtime de Windows.

### <a name="remarks"></a>Notes

Le `RoInitializeWrapper` classe appelle `Windows::Foundation::Initialize(flags)`.

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::~RoInitializeWrapper

Annule l’exécution de Windows.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Notes

Le `RoInitializeWrapper` classe appelle `Windows::Foundation::Uninitialize()`.
