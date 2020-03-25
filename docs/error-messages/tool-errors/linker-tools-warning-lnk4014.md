---
title: Avertissement des outils Éditeur de liens LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194276"
---
# <a name="linker-tools-warning-lnk4014"></a>Avertissement des outils Éditeur de liens LNK4014

Impossible de trouver l’objet membre "ObjectName"

LIB n’a pas pu trouver `objectname` dans la bibliothèque.

Les options **/Remove** et **/extract** requièrent le nom complet de l’objet membre qui doit être supprimé ou copié dans un fichier. Le nom complet comprend le chemin d’accès du fichier objet d’origine. Pour afficher les noms complets des objets membres dans une bibliothèque, utilisez DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) ou lib [/List](../../build/reference/managing-a-library.md).
