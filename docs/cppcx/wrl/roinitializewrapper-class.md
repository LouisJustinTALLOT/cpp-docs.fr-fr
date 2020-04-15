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
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371230"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper, classe

Initialise le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Notes

`RoInitializeWrapper`est une commodité qui initialise le Windows Runtime et renvoie un HRESULT qui indique si l’opération a été réussie. Parce que les appels `::Windows::Foundation::Uninitialize`des `RoInitializeWrapper` destructeurs de classe, les instances de doivent être déclarées à la portée globale ou de haut niveau.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                    | Description
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper:RoInitializeWrapper](#roinitializewrapper)        | Initialise une nouvelle instance de la classe `RoInitializeWrapper`.
[RoInitializeWrapper::RoInitializeWrapper](#tilde-roinitializewrapper) | Détruit l’instance actuelle `RoInitializeWrapper` de la classe.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                       | Description
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Récupère le HRESULT produit `RoInitializeWrapper` par le constructeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RoInitializeWrapper`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>RoInitializeWrapper::HRESULT()

Récupère la valeur HRESULT produite `RoInitializeWrapper` par le dernier constructeur.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>RoInitializeWrapper:RoInitializeWrapper

Initialise une nouvelle instance de la classe `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Paramètres

*Drapeaux*<br/>
L’un des recensements RO_INIT_TYPE, qui spécifie le support fourni par le Windows Runtime.

### <a name="remarks"></a>Notes

La `RoInitializeWrapper` classe `Windows::Foundation::Initialize(flags)`invoque .

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Uninitialise le Windows Runtime.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Notes

La `RoInitializeWrapper` classe `Windows::Foundation::Uninitialize()`invoque .
