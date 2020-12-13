---
description: 'En savoir plus sur : le marshaling'
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 2931bd9ab5e2fb8376ced44dd519a6de107be88e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152631"
---
# <a name="marshaling"></a>Marshaling

La technique COM de marshaling permet d’utiliser des interfaces exposées par un objet dans un processus dans un autre processus. Dans le marshaling, COM fournit du code (ou utilise le code fourni par l’implémenteur d’interface) pour empaqueter les paramètres d’une méthode dans un format qui peut être déplacé entre les processus (ainsi que, sur le réseau aux processus s’exécutant sur d’autres ordinateurs) et pour décompresser ces paramètres à l’autre extrémité. De même, COM doit effectuer ces mêmes étapes sur le retour de l’appel.

> [!NOTE]
> Le marshaling n’est généralement pas nécessaire quand une interface fournie par un objet est utilisée dans le même processus que l’objet. Toutefois, le marshaling peut être nécessaire entre les threads.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[Détails du marshaling](/windows/win32/com/marshaling-details)
