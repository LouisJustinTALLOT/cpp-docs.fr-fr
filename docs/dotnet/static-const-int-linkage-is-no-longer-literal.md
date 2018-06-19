---
title: Liaison static Const Int n’est plus littérale | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc3f72080c08807026c6458979ac0ba561e298df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164994"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>La liaison Static Const Int n'est plus littérale
Déclaration d’un membre constant d’une classe a été modifiée à partir des Extensions managées pour C++ vers Visual C++.  
  
 Bien que `static const` intégraux sont toujours pris en charge, leur attribut de chaînage a changé. Leur précédent attribut de chaînage est désormais porté par un membre intégral littéral. Par exemple, considérez la classe d’Extensions managées suivante :  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 Cela génère les attributs CIL sous-jacents suivants pour le champ (Notez l’attribut littéral) :  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Alors que cela se compile encore correctement dans la nouvelle syntaxe :  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 Il n’émet plus l’attribut littéral et par conséquent n’est pas considéré comme une constante par le runtime CLR :  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Afin d’avoir le même attribut littéral de langage à l’autre, la déclaration doit être modifiée pour qui vient d’être pris en charge `literal` membre de données, comme suit,  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations de membre dans une classe ou Interface (C + c++ / CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Littéral](../windows/literal-cpp-component-extensions.md)