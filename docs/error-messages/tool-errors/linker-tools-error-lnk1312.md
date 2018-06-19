---
title: Erreur LNK1312 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748276ed8fa459c41174f23d32bcef127cbdd510
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300444"
---
# <a name="linker-tools-error-lnk1312"></a>Erreur des outils Éditeur de liens LNK1312
fichier non valide ou endommagé : Impossible d’importer l’assembly  
  
 Lors de la création d’un assembly, un fichier autre qu’un module ou un assembly compilé avec **/CLR** a été passé à la **/ASSEMBLYMODULE** option de l’éditeur de liens.  Si vous avez passé un fichier objet à **/ASSEMBLYMODULE**, simplement passer l’objet directement à l’éditeur de liens, plutôt qu’à **/ASSEMBLYMODULE**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant créé le fichier .obj.  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur LNK1312.  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```