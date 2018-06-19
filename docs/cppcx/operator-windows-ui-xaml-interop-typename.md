---
title: opérateur Windows::UI::Xaml::Interop::TypeName | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 714d39a70b19998a5daddceadc2c91df65312122
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256264"
---
# <a name="operator-windowsuixamlinteroptypename"></a>Windows::UI::Xaml::Interop::TypeName, opérateur
Permet la conversion de `Platform::Type` en [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) quand un `Platform::Type^`est fourni.  
  
### <a name="remarks"></a>Notes  
 `TypeName` est la structure Windows Runtime indépendante du langage pour représenter les informations de type. [Platform::Type](../cppcx/platform-type-class.md) est spécifique à C++ et ne peut pas être passé à travers l'interface binaire d'application (ABI). Voici une utilisation de `TypeName`dans la fonction [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) :  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment convertir un `TypeName` en `Type`.  
  
```  
  
// Convert from Type to TypeName  
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Projet de programmes .NET Framework `TypeName` sous la forme [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True).  
  
### <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [opérateur Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type, classe](../cppcx/platform-type-class.md)