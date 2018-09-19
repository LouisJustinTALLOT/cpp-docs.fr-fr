---
title: Avertissement LNK4014 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df0a3b6f30733413a0f27c0b8daa07394bb04b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023109"
---
# <a name="linker-tools-warning-lnk4014"></a>Avertissement des outils Éditeur de liens LNK4014

Impossible de trouver l’objet membre « %{ObjectName/} »

LIB n’a pas trouvé `objectname` dans la bibliothèque.

Le **/supprimer** et **/extraire** options nécessitent le nom complet de l’objet de membre qui doit être supprimé ou copiées dans un fichier. Le nom complet inclut le chemin d’accès du fichier objet d’origine. Pour afficher les noms complets des objets membres dans une bibliothèque, utilisez DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) ou LIB [/la liste](../../build/reference/managing-a-library.md).