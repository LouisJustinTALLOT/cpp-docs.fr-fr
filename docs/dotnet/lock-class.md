---
title: Lock, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ef0887ca3eec7510717aab21ba4c6c7aba98d25
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380293"
---
# <a name="lock-class"></a>lock, classe

Cette classe automatise l’acquisition d’un verrou de synchroniser l’accès à un objet à partir de plusieurs threads.  Lorsqu’il est construit il acquiert le verrou et lorsqu’il détruit les versions le verrou.

## <a name="syntax"></a>Syntaxe

```
ref class lock;
```

## <a name="remarks"></a>Notes

`lock` est disponible uniquement pour les objets CLR et peut uniquement être utilisé dans le code CLR.

En interne, la classe du verrou utilise <xref:System.Threading.Monitor> pour synchroniser l’accès. Consultez cette rubrique pour plus d’informations sur la synchronisation.

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[lock](../dotnet/lock.md)<br/>
[lock, membres](../dotnet/lock-members.md)