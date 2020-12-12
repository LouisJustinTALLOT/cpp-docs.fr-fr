---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4102'
title: Avertissement des outils Éditeur de liens LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: b0977cfa89c0ddb5edbc7dc74428b774331a87e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294455"
---
# <a name="linker-tools-warning-lnk4102"></a>Avertissement des outils Éditeur de liens LNK4102

exportation du destructeur de suppression’name'; l’image risque de ne pas s’exécuter correctement

Le programme a tenté d’exporter un destructeur de suppression. La suppression résultante peut se produire dans une limite de DLL de telle sorte qu’un processus puisse libérer de la mémoire qu’il ne possède pas. Assurez-vous que le symbole donné n’est pas listé dans votre fichier. def et que le symbole n’est pas listé comme argument de l’option **/Import** ou **/Export** dans la ligne de commande de l’éditeur de liens.

Si vous reconstruisez la bibliothèque Runtime C, vous pouvez ignorer ce message.
