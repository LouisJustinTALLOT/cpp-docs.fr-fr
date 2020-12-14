---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2027'
title: Erreur des outils Éditeur de liens LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 006ca3b0c9d0ef85f118db9b562e8228c7cad238
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275761"
---
# <a name="linker-tools-error-lnk2027"></a>Erreur des outils Éditeur de liens LNK2027

Référence de module non résolue’module'

Un fichier passé à l’éditeur de liens a une dépendance sur un module qui n’a pas été spécifié avec **/ASSEMBLYMODULE** ou passé directement à l’éditeur de liens.

Pour résoudre LNK2027, effectuez l’une des opérations suivantes :

- Ne transmettez pas à l’éditeur de liens le fichier qui a la dépendance de module.

- Spécifiez le module avec **/ASSEMBLYMODULE**.

- Si le module est un. netmodule sécurisé, transmettez le module directement à l’éditeur de liens.

Pour plus d’informations, consultez [/ASSEMBLYMODULE (ajouter un module MSIL à l’assembly)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) et [fichiers. netmodule en tant qu’entrée dans l’éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).
