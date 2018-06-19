---
title: idl_module | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11547a3fb1bd46a1e2edb8ce9dd0a6547464f796
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882522"
---
# <a name="idlmodule"></a>idl_module
Spécifie un point d’entrée dans un fichier .dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ idl_module (   
   name=module_name,   
   dllname=dll,   
   uuid="uuid",   
   helpstring="help text",   
   helpstringcontext=helpcontextID,   
   helpcontext=helpcontext,   
   hidden,   
   restricted  
) ]  
function declaration  
```  
  
#### <a name="parameters"></a>Paramètres  
 **name**  
 Un nom défini par l’utilisateur pour le bloc de code qui s’affiche dans le fichier .idl.  
  
 **dllname** (facultatif)  
 Le fichier .dll qui contient l’exportation.  
  
 `uuid`(facultatif)  
 ID unique.  
  
 **HelpString** (facultatif)  
 Une chaîne de caractères utilisée pour décrire la bibliothèque de types.  
  
 **helpstringcontext** (facultatif)  
 L’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.  
  
 **helpcontext** (facultatif)  
 ID d’aide pour cette bibliothèque de types.  
  
 **hidden** (facultatif)  
 Un paramètre qui empêche l’affichage de la bibliothèque. Pour plus d’informations, consultez l’attribut MIDL [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) .  
  
 ***restreint*** (facultatif)  
 Membres de la bibliothèque ne peut pas être appelées arbitrairement. Pour plus d’informations, consultez l’attribut MIDL [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) .  
  
 *déclaration de fonction*  
 La fonction que vous allez définir.  
  
## <a name="remarks"></a>Notes  
 Le `idl_module` attribut C++ vous permet de spécifier le point d’entrée dans un fichier .dll, ce qui permet d’importer à partir d’un fichier .dll.  
  
 Le **idl_module** attribut a des fonctionnalités similaires à la [module](http://msdn.microsoft.com/library/windows/desktop/aa367099) attribut MIDL.  
  
 Vous pouvez exporter quoi que ce soit à partir d’un objet COM que vous pouvez exporter à partir d’un fichier .dll en plaçant un point d’entrée DLL dans le bloc de bibliothèque d’un fichier .idl.  
  
 Votre doit utiliser `idl_module` en deux étapes. Tout d’abord, vous devez définir une paire nom/DLL. Ensuite, lorsque vous utilisez `idl_module` pour spécifier un point d’entrée, spécifiez le nom et des attributs supplémentaires.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le `idl_module` attribut :  
  
```  
// cpp_attr_ref_idl_module.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];  
[idl_module(name="MyLib"), entry(4), usesgetlasterror]  
void FuncName(int i);  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|N'importe où|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   
 [entry](../windows/entry.md)   
