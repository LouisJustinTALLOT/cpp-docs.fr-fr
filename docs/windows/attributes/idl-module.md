---
title: idl_module (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 651d2e133d7ef08fce48feded1b7a5aff458adb1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845222"
---
# <a name="idl_module"></a>idl_module

Spécifie un point d’entrée dans un fichier. dll.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Paramètres

*name*<br/>
Nom défini par l’utilisateur pour le bloc de code qui s’affiche dans le fichier. idl.

*DllName*<br/>
Facultatif Fichier. dll qui contient l’exportation.

*uuid*<br/>
Facultatif ID unique.

*helpstring*<br/>
Facultatif Chaîne de caractères utilisée pour décrire la bibliothèque de types.

*helpstringcontext*<br/>
Facultatif ID d’une rubrique d’aide dans un fichier. hlp ou. chm.

*helpcontext*<br/>
Facultatif ID d’aide pour cette bibliothèque de types.

*masquer*<br/>
Facultatif Paramètre qui empêche l’affichage de la bibliothèque. Pour plus d’informations, consultez l’attribut MIDL [hidden](/windows/win32/Midl/hidden) .

*sensible*<br/>
Facultatif Les membres de la bibliothèque ne peuvent pas être appelés de façon arbitraire. Pour plus d’informations, consultez l’attribut MIDL [restricted](/windows/win32/Midl/restricted) .

*Déclaration de fonction*<br/>
Fonction que vous allez définir.

## <a name="remarks"></a>Notes

L’attribut **idl_module** C++ vous permet de spécifier le point d’entrée dans un fichier. dll, ce qui vous permet d’importer à partir d’un fichier. dll.

L’attribut **idl_module** possède des fonctionnalités similaires à l’attribut MIDL du [module](/windows/win32/Midl/module) .

Vous pouvez exporter n’importe quoi à partir d’un objet COM que vous pouvez exporter à partir d’un fichier. dll en plaçant un point d’entrée de DLL dans le bloc de bibliothèque d’un fichier. idl.

Vous devez utiliser **idl_module** en deux étapes. Tout d’abord, vous devez définir une paire nom/DLL. Ensuite, lorsque vous utilisez **idl_module** pour spécifier un point d’entrée, spécifiez le nom et d’autres attributs.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l’attribut **idl_module** :

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)<br/>
[mention](entry.md)
