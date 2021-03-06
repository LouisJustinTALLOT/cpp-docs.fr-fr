---
description: 'En savoir plus sur : classe RoInitializeWrapper'
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
ms.openlocfilehash: b7f2c49bd461f08ad732680f1a02968ee7717116
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319298"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper, classe

Initialise le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Notes

`RoInitializeWrapper` est un confort qui initialise la Windows Runtime et retourne un HRESULT qui indique si l’opération a réussi. Étant donné que le destructeur de classe appelle `::Windows::Foundation::Uninitialize` , les instances de `RoInitializeWrapper` doivent être déclarées dans la portée globale ou de niveau supérieur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                                    | Description
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper :: RoInitializeWrapper](#roinitializewrapper)        | Initialise une nouvelle instance de la classe `RoInitializeWrapper`.
[RoInitializeWrapper :: ~ RoInitializeWrapper](#tilde-roinitializewrapper) | Détruit l’instance actuelle de la `RoInitializeWrapper` classe.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                       | Description
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper :: HRESULT ()](#hresult) | Récupère le HRESULT produit par le `RoInitializeWrapper` constructeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RoInitializeWrapper`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a> RoInitializeWrapper :: HRESULT ()

Récupère la valeur HRESULT produite par le dernier `RoInitializeWrapper` constructeur.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a> RoInitializeWrapper :: RoInitializeWrapper

Initialise une nouvelle instance de la classe `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
L’une des énumérations RO_INIT_TYPE, qui spécifie la prise en charge fournie par le Windows Runtime.

### <a name="remarks"></a>Notes

La `RoInitializeWrapper` classe appelle `Windows::Foundation::Initialize(flags)` .

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a> RoInitializeWrapper :: ~ RoInitializeWrapper

Réinitialise l’Windows Runtime.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Notes

La `RoInitializeWrapper` classe appelle `Windows::Foundation::Uninitialize()` .
