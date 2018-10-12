---
title: invalid_oversubscribe_operation, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1728053c7b42afedb4cda9b2dc96a089750a866
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161695"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation, classe

Cette classe décrit une exception levée quand le `Context::Oversubscribe` méthode est appelée avec le `_BeginOversubscription` paramètre défini sur **false** sans un appel antérieur à la `Context::Oversubscribe` méthode avec le `_BeginOversubscription` paramètre défini sur **true**.

## <a name="syntax"></a>Syntaxe

```
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Surchargé. Construit un objet `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> invalid_oversubscribe_operation

Construit un objet `invalid_oversubscribe_operation`.

```
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
