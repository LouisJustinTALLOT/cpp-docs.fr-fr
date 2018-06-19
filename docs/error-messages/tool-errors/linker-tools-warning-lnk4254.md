---
title: LNK4254 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb57882ab4269c06a53ed73fed2a9d6caf2f2c85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316892"
---
# <a name="linker-tools-warning-lnk4254"></a>Avertissement des outils Éditeur de liens LNK4254
section 'section1' (offset) fusionnée dans 'section2' (offset) avec des attributs différents  
  
 Le contenu d’une section ont été fusionné dans un autre, mais les attributs des deux sections sont différents. Votre programme peut provoquer des résultats inattendus. Par exemple, vous souhaitez lire des données uniquement peuvent maintenant être dans une section accessible en écriture.  
  
 Pour résoudre l’erreur LNK4254, modifier ou supprimer la demande de fusion.  
  
 Lorsque vous ciblez x86 ordinateurs et des cibles Windows CE (ARM, MIPS, SH4 et Thumb) avec Visual C++, le. CRT est en lecture seule. Si votre code dépend du comportement précédent (. CRT sont en lecture/écriture), vous pouvez constater un comportement inattendu.  
  
 Pour plus d'informations, consultez  
  
-   [/MERGE (Combiner des sections)](../../build/reference/merge-combine-sections.md)  
  
-   [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur LNK4254.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```