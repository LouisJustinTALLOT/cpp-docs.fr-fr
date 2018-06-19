---
title: LNK4014 d’avertissement des outils Éditeur de liens | Documents Microsoft
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
ms.openlocfilehash: 2fb86efbdc70342861a87a233ab687f7564cb48b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300057"
---
# <a name="linker-tools-warning-lnk4014"></a>Avertissement des outils Éditeur de liens LNK4014
Impossible de trouver l’objet membre « %{ObjectName/} »  
  
 LIB n’a pas pu trouver `objectname` dans la bibliothèque.  
  
 Le **/suppression de** et **/extraire** options requièrent le nom complet de l’objet membre qui doit être supprimé ou copié vers un fichier. Le nom complet inclut le chemin d’accès du fichier objet d’origine. Pour afficher les noms complets des objets membres d’une bibliothèque, utilisez DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) ou LIB [/liste](../../build/reference/managing-a-library.md).