---
title: Erreur LNK2033 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2033
dev_langs:
- C++
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d03e8d2e0502d6e3664bff05c75fffb4f4ebd5da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301968"
---
# <a name="linker-tools-error-lnk2033"></a>Erreur des outils Éditeur de liens LNK2033
jeton typeref non résolu (jeton) pour 'type'  
  
 Un type ne possède pas une définition dans les métadonnées MSIL.  
  
 LNK2033 peut se produire lors de la compilation avec **/CLR : safe** et où il n’existe qu’une déclaration anticipée d’un type dans un module MSIL, où le type est référencé dans le module MSIL.  
  
 Le type doit être défini sous **/CLR : safe**.  
  
 Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur LNK2033.  
  
```  
// LNK2033.cpp  
// compile with: /clr:safe  
// LNK2033 expected  
ref class A;  
ref class B {};  
  
int main() {  
   A ^ aa = nullptr;  
   B ^ bb = nullptr;   // OK  
};  
```