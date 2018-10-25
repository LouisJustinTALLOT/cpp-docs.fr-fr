---
title: idl_module (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 54fcef3c7b2ef86273a570e483f65b34b3b2efc2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063094"
---
# <a name="idlmodule"></a>idl_module

Spécifie un point d’entrée dans un fichier .dll.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Paramètres

*name*<br/>
Un nom défini par l’utilisateur du bloc de code qui s’affiche dans le fichier .idl.

*dllname*<br/>
(Facultatif) Le fichier .dll qui contient l’exportation.

*uuid*<br/>
(Facultatif) Un ID unique.

*helpstring*<br/>
(Facultatif) Une chaîne de caractères utilisée pour décrire la bibliothèque de types.

*helpstringcontext*<br/>
(Facultatif) L’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.

*helpcontext*<br/>
(Facultatif) L’ID d’aide pour cette bibliothèque de types.

*hidden*<br/>
(Facultatif) Un paramètre qui empêche l’affichage de la bibliothèque. Pour plus d’informations, consultez l’attribut MIDL [hidden](/windows/desktop/Midl/hidden) .

*restricted*<br/>
(Facultatif) Membres de la bibliothèque ne peut pas être appelées arbitrairement. Pour plus d’informations, consultez l’attribut MIDL [restricted](/windows/desktop/Midl/restricted) .

*déclaration de fonction*<br/>
La fonction que vous définirez.

## <a name="remarks"></a>Notes

Le **idl_module** attribut C++ vous permet de spécifier le point d’entrée dans un fichier .dll, qui vous permet d’importer à partir d’un fichier .dll.

Le **idl_module** attribut a des fonctionnalités similaires à la [module](/windows/desktop/Midl/module) attribut MIDL.

Vous pouvez exporter quoi que ce soit à partir d’un objet COM que vous pouvez exporter à partir d’un fichier .dll en plaçant un point d’entrée DLL dans le bloc de bibliothèque d’un fichier .idl.

Votre doit utiliser **idl_module** en deux étapes. Tout d’abord, vous devez définir une paire nom/DLL. Ensuite, lorsque vous utilisez **idl_module** pour spécifier un point d’entrée, spécifiez le nom et des attributs supplémentaires.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le **idl_module** attribut :

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[entry](entry.md)