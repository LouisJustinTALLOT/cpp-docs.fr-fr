---
title: LNK1179 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72a531397c3c101fbff937f293f772c5f6778523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300213"
---
# <a name="linker-tools-error-lnk1179"></a>Erreur des outils Éditeur de liens LNK1179
fichier non valide ou endommagé : COMDAT 'NomFichier' dupliqué  
  
 Un module objet contenait deux ou plusieurs COMDAT portant le même nom.  
  
 Cette erreur peut être dû à l’aide de [/H](../../build/reference/h-restrict-length-of-external-names.md), ce qui limite la longueur des noms externes, et [/Gy](../../build/reference/gy-enable-function-level-linking.md), qui regroupe les fonctions dans les COMDAT.  
  
## <a name="example"></a>Exemple  
 Dans le code suivant, `function1` et `function2` sont identiques dans les huit premiers caractères. La compilation avec **/Gy** et **H8** génère une erreur de liaison.  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```