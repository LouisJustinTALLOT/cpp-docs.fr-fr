---
title: Avertissement des outils Éditeur de liens LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183304"
---
# <a name="linker-tools-warning-lnk4102"></a>Avertissement des outils Éditeur de liens LNK4102

exportation du destructeur de suppression’name'; l’image risque de ne pas s’exécuter correctement

Le programme a tenté d’exporter un destructeur de suppression. La suppression résultante peut se produire dans une limite de DLL de telle sorte qu’un processus puisse libérer de la mémoire qu’il ne possède pas. Assurez-vous que le symbole donné n’est pas listé dans votre fichier. def et que le symbole n’est pas listé comme argument de l’option **/Import** ou **/Export** dans la ligne de commande de l’éditeur de liens.

Si vous reconstruisez la bibliothèque Runtime C, vous pouvez ignorer ce message.
