---
title: Avertissement LNK4102 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaffc4ddfa9a869c2e60e2c05dc2b7e296d94b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031852"
---
# <a name="linker-tools-warning-lnk4102"></a>Avertissement des outils Éditeur de liens LNK4102

exportation de la suppression de destructeur 'nom' ; image peut ne pas fonctionne correctement

Le programme a tenté d’exporter un destructeur de suppression. La suppression qui en résulte peut se produire sur une limite DLL, telles qu’un processus peut libérer la mémoire qu’il ne possède pas. Assurez-vous que le symbole donné n’est pas répertorié dans le fichier .def, et que le symbole n’est pas répertorié en tant qu’argument de la **/importation** ou **/EXPORT** option dans la ligne de commande de l’éditeur de liens.

Si vous régénérez la bibliothèque Runtime C, vous pouvez ignorer ce message.