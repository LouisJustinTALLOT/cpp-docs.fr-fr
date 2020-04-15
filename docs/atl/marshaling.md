---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319352"
---
# <a name="marshaling"></a>Marshaling

La technique COM de marshaling permet d’utiliser les interfaces exposées par un objet dans un processus. En marshaling, COM fournit du code (ou utilise le code fourni par l’implémentateur d’interface) à la fois pour emballer les paramètres d’une méthode dans un format qui peut être déplacé à travers les processus (ainsi que, à travers le fil pour les processus en cours d’exécution sur d’autres machines) et pour déballer ces paramètres à l’autre extrémité. De même, COM doit effectuer ces mêmes étapes au retour de l’appel.

> [!NOTE]
> Le marshaling n’est généralement pas nécessaire lorsqu’une interface fournie par un objet est utilisée dans le même processus que l’objet. Cependant, le marshaling peut être nécessaire entre les fils.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[Détails de marshaling](/windows/win32/com/marshaling-details)
