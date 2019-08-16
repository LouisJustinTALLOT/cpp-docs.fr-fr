---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492041"
---
# <a name="marshaling"></a>Marshaling

La technique COM de marshaling permet d’utiliser des interfaces exposées par un objet dans un processus dans un autre processus. Dans le marshaling, COM fournit du code (ou utilise le code fourni par l’implémenteur d’interface) pour empaqueter les paramètres d’une méthode dans un format qui peut être déplacé entre les processus (ainsi que, sur le réseau aux processus s’exécutant sur d’autres ordinateurs) et pour décompresser ces paramètres à l’autre extrémité. De même, COM doit effectuer ces mêmes étapes sur le retour de l’appel.

> [!NOTE]
>  Le marshaling n’est généralement pas nécessaire quand une interface fournie par un objet est utilisée dans le même processus que l’objet. Toutefois, le marshaling peut être nécessaire entre les threads.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Détails du marshaling](/windows/win32/com/marshaling-details)
