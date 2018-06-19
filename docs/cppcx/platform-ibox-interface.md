---
title: Interface Platform::IBox | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7894eceb2f345303400eec9b0490db58b3c3583f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089521"
---
# <a name="platformibox-interface"></a>Platform::IBox, interface
L'interface [Platform::IBox](../cppcx/platform-ibox-interface.md) est le nom C++ de l'interface `Windows::Foundation::IReference` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Type de la valeur boxed.  
  
### <a name="remarks"></a>Notes  
 L'interface `IBox<T>` est principalement utilisée en interne pour représenter les types de valeur Nullable, comme décrit dans [Classes et structs value (C++/CX)](../cppcx/value-classes-and-structs-c-cx.md). L'interface est aussi utilisée en interne pour effectuer un boxing des types valeur passés aux méthodes C++ qui prennent des paramètres de type `Object^`. Vous pouvez déclarer explicitement un paramètre d'entrée comme `IBox<SomeValueType>`. Pour obtenir un exemple, consultez [Boxing](../cppcx/boxing-c-cx.md).  
  
### <a name="requirements"></a>Spécifications  
  
### <a name="members"></a>Membres  
 L'interface `Platform::IBox` hérite de l'interface [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) . `IBox` a ces membres :  
  
 **Propriétés**  
  
|Méthode|Description|  
|------------|-----------------|  
|[Valeur](#value)|Retourne une valeur unboxed qui a été précédemment enregistrée dans cette instance `IBox` .|  

## <a name="value"></a> Ibox::value, propriété
Retourne la valeur qui a été enregistrée à l'origine dans cet objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>Paramètres  
 `T`  
 Type de la valeur boxed.  
  
### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Retourne la valeur qui a été enregistrée à l'origine dans cet objet.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir un exemple, consultez [Boxing](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)