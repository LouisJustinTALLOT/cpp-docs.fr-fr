---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 0661a4cdde0a3a875cf27221e884f6c65b9fea55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262383"
---
# <a name="marshaling"></a>Marshaling

La technique COM du marshaling permet aux interfaces exposées par un objet dans un seul processus à utiliser dans un autre processus. Dans le marshaling, COM fournit du code (ou utilise le code fourni par l’implémenteur d’interface) pour compresser les paramètres d’une méthode dans un format qui peut être déplacé entre processus (ainsi que, sur le réseau pour les processus exécutés sur d’autres ordinateurs) et à décompresser ces paramètres à l’autre extrémité. De même, COM doit effectuer ces mêmes étapes sur le retour de l’appel.

> [!NOTE]
>  Marshaling est généralement pas nécessaire quand une interface fournie par un objet est utilisée dans le même processus que l’objet. Toutefois, le marshaling peut être nécessaire entre les threads.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Détails de marshaling](/windows/desktop/com/marshaling-details)
