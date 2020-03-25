---
title: HelpContext (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 292db21e8092284a92b09ef3f889bb0475d0d886
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167002"
---
# <a name="helpcontext"></a>helpcontext

Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier **d’aide** .

## <a name="syntax"></a>Syntaxe

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Paramètres

*id*<br/>
ID de contexte de la rubrique d’aide. Pour plus d’informations sur les ID de contexte, consultez [aide HTML : aide contextuelle pour vos programmes](../../mfc/html-help-context-sensitive-help-for-your-programs.md) .

## <a name="remarks"></a>Notes

L’attribut **HelpContext** C++ a les mêmes fonctionnalités que l’attribut MIDL de [HelpContext](/windows/win32/Midl/helpcontext) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **HelpContext**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
