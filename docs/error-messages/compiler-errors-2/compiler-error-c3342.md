---
title: Erreur du compilateur C3342 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3342
dev_langs: C++
helpviewer_keywords: C3342
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31a3aead6f2e445a30532a5840f22ac588bd4d4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3342"></a>Erreur du compilateur C3342
'attribute' : attribut ambigu  
  
 Le compilateur a détecté plusieurs définitions d’un attribut.  
  
 Un attribut a été défini plusieurs fois.  
  
 Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3342 :  
  
```  
// C3342.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Reflection;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class XAttribute : public  Attribute {};  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class X : public Attribute {};  
  
[X]   // C3342 could refer to X or XAttribute  
// try the following line instead  
// [XAttribute]  
public ref class Class4 {};  
```