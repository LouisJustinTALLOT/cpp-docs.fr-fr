---
title: accelerator_view_removed, classe
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127122"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed, classe

Exception levée lorsqu’un appel DirectX sous-jacent échoue en raison du mécanisme de détection et de récupération du délai d’attente de Windows.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur accelerator_view_removed](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view_removed`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Retourne un code d’erreur HRESULT indiquant la cause de la suppression de l’objet `accelerator_view`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="ctor"></a>accelerator_view_removed

Initialise une nouvelle instance de la classe [accelerator_view_removed](accelerator-view-removed-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Paramètres

*message*<br/>
Description de l’erreur.

*view_removed_reason*<br/>
Code d’erreur HRESULT indiquant la cause de la suppression de l’objet `accelerator_view`.

### <a name="return-value"></a>Valeur de retour

Nouvelle instance de la classe `accelerator_view_removed`.

## <a name="get_view_removed_reason"></a>get_view_removed_reason

Retourne un code d’erreur HRESULT indiquant la cause de la suppression de l’objet `accelerator_view`.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
