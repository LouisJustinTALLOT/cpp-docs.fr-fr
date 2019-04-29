---
title: Avertissement des outils Éditeur de liens LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327260"
---
# <a name="linker-tools-warning-lnk4102"></a>Avertissement des outils Éditeur de liens LNK4102

exportation de la suppression de destructeur 'nom' ; image peut ne pas fonctionne correctement

Le programme a tenté d’exporter un destructeur de suppression. La suppression qui en résulte peut se produire sur une limite DLL, telles qu’un processus peut libérer la mémoire qu’il ne possède pas. Assurez-vous que le symbole donné n’est pas répertorié dans le fichier .def, et que le symbole n’est pas répertorié en tant qu’argument de la **/importation** ou **/EXPORT** option dans la ligne de commande de l’éditeur de liens.

Si vous régénérez la bibliothèque Runtime C, vous pouvez ignorer ce message.