---
title: Avertissement (niveau 4) du compilateur C4001 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc728fa5c66fb4b42c8fe4a785f36048ffbaed4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292657"
---
# <a name="compiler-warning-level-4-c4001"></a>Avertissement (niveau 4) du compilateur C4001
extension non standard 'commentaire sur une ligne unique' a été utilisée.  

> [!NOTE] 
> Cet avertissement est supprimé dans Visual Studio 2017 version 15.5 commentaires sur une ligne étant C99 standard.
  
 Commentaires sur une ligne sont standard en C++ et C en commençant par C99 standard. Sous compatibilité ANSI stricte ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), les fichiers C qui contiennent des commentaires sur une ligne, génèrent l’avertissement C4001 en raison de l’utilisation d’une extension non standard. Étant donné que les commentaires sur une ligne sont standard en C++, les fichiers C contenant des commentaires sur une ligne ne produisent pas C4001 lors de la compilation avec les extensions Microsoft (/Ze).  
  
## <a name="example"></a>Exemple  
 Pour désactiver l’avertissement, supprimez les commentaires [#pragma warning(disable:4001)](../../preprocessor/warning.md).  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```