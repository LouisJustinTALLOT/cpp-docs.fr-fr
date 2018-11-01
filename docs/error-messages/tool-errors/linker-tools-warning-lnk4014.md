---
title: Avertissement des outils Éditeur de liens LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: f67990ed74f500f1b954edcf1d6437f64f93f0d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511705"
---
# <a name="linker-tools-warning-lnk4014"></a>Avertissement des outils Éditeur de liens LNK4014

Impossible de trouver l’objet membre « %{ObjectName/} »

LIB n’a pas trouvé `objectname` dans la bibliothèque.

Le **/supprimer** et **/extraire** options nécessitent le nom complet de l’objet de membre qui doit être supprimé ou copiées dans un fichier. Le nom complet inclut le chemin d’accès du fichier objet d’origine. Pour afficher les noms complets des objets membres dans une bibliothèque, utilisez DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) ou LIB [/la liste](../../build/reference/managing-a-library.md).