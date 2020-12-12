---
description: 'En savoir plus sur : classe accelerator_view_removed'
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
ms.openlocfilehash: 86a5b89d3b8065bccd8eec8b10bade9ed26d6a05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254493"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed, classe

Exception levée lorsqu’un appel DirectX sous-jacent échoue en raison du mécanisme de détection et de récupération du délai d’attente de Windows.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur accelerator_view_removed](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view_removed`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Retourne un code d’erreur HRESULT indiquant la cause de la suppression de l' `accelerator_view` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="accelerator_view_removed"></a><a name="ctor"></a> accelerator_view_removed

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
Code d’erreur HRESULT indiquant la cause de la suppression de l' `accelerator_view` objet.

### <a name="return-value"></a>Valeur renvoyée

Nouvelle instance de la classe `accelerator_view_removed`.

## <a name="get_view_removed_reason"></a><a name="get_view_removed_reason"></a> get_view_removed_reason

Retourne un code d’erreur HRESULT indiquant la cause de la suppression de l' `accelerator_view` objet.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
