---
title: Type d’opérateur ^ | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8abccf48219b70040ce728ba0dff9fa02b57bfc0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688463"
---
# <a name="operator-type"></a>Type^, opérateur
Permet la conversion de [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) à `Platform::Type`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `Platform::Type` en fonction d’un [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
### <a name="remarks"></a>Notes  
 `TypeName` est la structure Windows Runtime indépendante du langage pour représenter les informations de type. [Platform::Type](../cppcx/platform-type-class.md) est spécifique à C++ et ne peut pas être passé à travers l'interface binaire d'application (ABI). Voici une utilisation de `TypeName`, dans le [Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) fonction :  
  
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
 Projet de programmes .NET framework `TypeName` en tant que <xref:System.Type>
  
### <a name="requirements"></a>Configuration requise  
  
## <a name="see-also"></a>Voir aussi  
 [opérateur Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type, classe](../cppcx/platform-type-class.md)