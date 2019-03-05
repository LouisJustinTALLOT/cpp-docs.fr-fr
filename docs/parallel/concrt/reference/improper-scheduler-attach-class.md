---
title: improper_scheduler_attach, classe
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
ms.openlocfilehash: 2d6a7b53269d305c976bcc596fe85dc018442332
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271539"
---
# <a name="improperschedulerattach-class"></a>improper_scheduler_attach, classe

Cette classe décrit une exception levée quand la méthode `Attach` est appelée sur un objet `Scheduler` qui est déjà attaché au contexte actuel.

## <a name="syntax"></a>Syntaxe

```
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|Surchargé. Construit un objet `improper_scheduler_attach`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> improper_scheduler_attach

Construit un objet `improper_scheduler_attach`.

```
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
