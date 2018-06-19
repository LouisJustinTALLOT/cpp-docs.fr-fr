---
title: Erreur irrécupérable C1107 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1107
dev_langs:
- C++
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 949ee09244a106984522fb35dd13c0b3426fc820
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199929"
---
# <a name="fatal-error-c1107"></a>Erreur irrécupérable C1107
Impossible de trouver l’assembly 'fichier' : spécifiez le chemin de recherche en utilisant /AI ou en définissant la variable d’environnement LIBPATH  
  
 Un fichier de métadonnées a été passé à un [#using](../../preprocessor/hash-using-directive-cpp.md) directive le compilateur n’a pas pu localiser.  
  
 LIBPATH, qui est décrite dans la rubrique de `#using`et le [/AI](../../build/reference/ai-specify-metadata-directories.md) option du compilateur permettent de spécifier les répertoires dans lesquels le compilateur recherche les fichiers de métadonnées référencés.