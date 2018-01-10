---
title: "Type d’opérateur ^ | Documents Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8d51699d56f1868d5840665017feba2dec50766
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="operator-type"></a>Type^, opérateur
Permet la conversion de [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) en `Platform::Type`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `Platform::Type` quand un [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)est fourni.  
  
### <a name="remarks"></a>Notes  
 `TypeName` est la structure Windows Runtime indépendante du langage pour représenter les informations de type. [Platform::Type](../cppcx/platform-type-class.md) est spécifique à C++ et ne peut pas être passé à travers l'interface binaire d'application (ABI). Voici une utilisation de `TypeName`dans la fonction [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) :  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment convertir un `TypeName` en `Type`.  
  
```  
  
// Convert from Type to TypeName  
TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Projet de programmes .NET Framework `TypeName` sous la forme [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True).  
  
### <a name="requirements"></a>Configuration requise  
  
## <a name="see-also"></a>Voir aussi  
 [Windows::UI::Xaml::Interop::TypeName, opérateur](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)   
 [Platform::Type, classe](../cppcx/platform-type-class.md)