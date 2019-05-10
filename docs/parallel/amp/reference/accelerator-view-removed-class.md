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
ms.openlocfilehash: eddcf44966d197068113c5e7817dad37841261a3
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524846"
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed, classe

Exception levée lorsqu’un appel DirectX sous-jacent échoue en raison de la détection et la récupération un mécanisme de délai d’attente Windows.

## <a name="syntax"></a>Syntaxe

```
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[accelerator_view_removed, constructeur](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view_removed`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Retourne un code d’erreur HRESULT indiquant la cause de le `accelerator_view` suppression de l’objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Configuration requise

**En-tête :** amprt.h

**Espace de noms :** Concurrence

## <a name="ctor"></a> accelerator_view_removed

Initialise une nouvelle instance de la [accelerator_view_removed](accelerator-view-removed-class.md) classe.

### <a name="syntax"></a>Syntaxe

```
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Paramètres

*message*<br/>
Description de l'erreur.

*view_removed_reason*<br/>
Un code d’erreur HRESULT indiquant la cause de la suppression de la `accelerator_view` objet.

### <a name="return-value"></a>Valeur de retour

Nouvelle instance de la classe `accelerator_view_removed`.

## <a name="get_view_removed_reason"></a> get_view_removed_reason

Retourne un code d’erreur HRESULT indiquant la cause de le `accelerator_view` suppression de l’objet.

### <a name="syntax"></a>Syntaxe

```
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
