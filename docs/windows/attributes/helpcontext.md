---
description: 'En savoir plus sur : HelpContext'
title: HelpContext (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: cfedec2f7650490dd266331e6853ba47265aa4ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335720"
---
# <a name="helpcontext"></a>helpcontext

Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier **d’aide** .

## <a name="syntax"></a>Syntaxe

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Paramètres

*id*<br/>
ID de contexte de la rubrique d’aide. Pour plus d’informations sur les ID de contexte, consultez [aide HTML : Context-Sensitive de l’aide pour vos programmes](../../mfc/html-help-context-sensitive-help-for-your-programs.md) .

## <a name="remarks"></a>Notes

L’attribut C++ de **HelpContext** a les mêmes fonctionnalités que l’attribut MIDL de [HelpContext](/windows/win32/Midl/helpcontext) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [DefaultValue](defaultvalue.md) pour obtenir un exemple d’utilisation de **HelpContext**.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**, **`typedef`** , **`class`** , méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
