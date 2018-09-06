---
title: Macros de Conversion de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4df562e693a412ca93720748f929d1bbcefc829
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760459"
---
# <a name="string-conversion-macros"></a>Macros de Conversion de chaînes

Ces macros fournissent des fonctionnalités de conversion chaîne.  

##  <a name="atl_and_mfc_string_conversion_macros"></a>  Macros de Conversion de chaîne MFC et ATL

Les macros de conversion de chaînes présentées ici sont valides à la fois pour ATL et pour MFC. Pour plus d’informations sur la conversion de chaînes MFC, consultez [TN059 : utilisation de Macros de Conversion MBCS/Unicode MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) et [MFC Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  Macros de Conversion de chaîne TEXTMETRIC et DEVMODE

Ces macros créent une copie d’un [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) ou [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) structurer et convertir les chaînes au sein de la nouvelle structure en un nouveau type de chaîne. Les macros allouer de mémoire sur la pile pour la nouvelle structure et retournent un pointeur vers la nouvelle structure.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Notes

Exemple :

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

et

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

Dans les noms des macros, le type de chaîne dans la structure de la source est sur la gauche (par exemple, **A**) et le type de chaîne dans la structure de destination se trouve à droite (par exemple, **W**). **Un** LPSTR, l’acronyme **OLE** LPOLESTR, l’acronyme **T** LPTSTR, l’acronyme et **W** est l’acronyme LPWSTR.

Par conséquent, DEVMODEA2W copie un `DEVMODE` structure avec LPSTR chaînes en un `DEVMODE` structure avec des chaînes LPWSTR, TEXTMETRICOLE2T copies un `TEXTMETRIC` structure avec LPOLESTR chaînes en un `TEXTMETRIC` structure avec des chaînes de LPTSTR et ainsi de suite.

Les deux chaînes converties dans le `DEVMODE` structure sont le nom du périphérique (`dmDeviceName`) et le nom du formulaire (`dmFormName`). Le `DEVMODE` macros de conversion de chaîne également les mettre à jour la taille de la structure (`dmSize`).

Les quatre chaînes converties dans le `TEXTMETRIC` structure sont le premier caractère (`tmFirstChar`), le dernier caractère (`tmLastChar`), le caractère par défaut (`tmDefaultChar`) et le caractère de saut (`tmBreakChar`).

Le comportement de la `DEVMODE` et `TEXTMETRIC` macros de conversion de chaînes dépend de la directive de compilateur en vigueur, le cas échéant. Si les types source et de destination sont les mêmes, aucune conversion n'est effectuée. Modifier des directives de compilateur **T** et **OLE** comme suit :

|Directive du compilateur appliquée|T devient|OLE devient|
|----------------------------------|---------------|-----------------|
|none|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|**\_UNICODE** et **OLE2ANSI**|**W**|**A**|

Le tableau suivant répertorie les `DEVMODE` et `TEXTMETRIC` macros de conversion de chaîne.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|  

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
