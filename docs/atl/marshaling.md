---
title: Marshaling | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69f1b7e131b614aa4714f0c2be19fab79982031c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108623"
---
# <a name="marshaling"></a>Marshaling

La technique COM du marshaling permet aux interfaces exposées par un objet dans un seul processus à utiliser dans un autre processus. Dans le marshaling, COM fournit du code (ou utilise le code fourni par l’implémenteur d’interface) pour compresser les paramètres d’une méthode dans un format qui peut être déplacé entre processus (ainsi que, sur le réseau pour les processus exécutés sur d’autres ordinateurs) et à décompresser ces paramètres à l’autre extrémité. De même, COM doit effectuer ces mêmes étapes sur le retour de l’appel.

> [!NOTE]
>  Marshaling est généralement pas nécessaire quand une interface fournie par un objet est utilisée dans le même processus que l’objet. Toutefois, le marshaling peut être nécessaire entre les threads.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Détails de marshaling](/windows/desktop/com/marshaling-details)

