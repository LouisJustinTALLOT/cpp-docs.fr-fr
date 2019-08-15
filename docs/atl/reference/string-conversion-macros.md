---
title: Macros de conversion de chaînes
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: f7d9548fc5710e8d3d5d668dff230a60e7a291a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495190"
---
# <a name="string-conversion-macros"></a>Macros de conversion de chaînes

Ces macros fournissent des fonctionnalités de conversion de chaînes.

##  <a name="atl_and_mfc_string_conversion_macros"></a>Macros de conversion de chaînes ATL et MFC

Les macros de conversion de chaînes présentées ici sont valides à la fois pour ATL et pour MFC. Pour plus d’informations sur la conversion de chaînes [MFC, consultez TN059: À l’aide](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) des macros de conversion MFC MBCS/Unicode et des [macros et globales MFC](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>Macros de conversion de chaînes DEVMODE et TEXTMETRIC

Ces macros créent une copie d’une structure [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) ou [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) et convertissent les chaînes dans la nouvelle structure en un nouveau type de chaîne. Les macros allouent de la mémoire sur la pile pour la nouvelle structure et retournent un pointeur vers la nouvelle structure.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Notes

Par exemple :

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

et

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

Dans les noms de macros, le type de chaîne dans la structure source est à gauche (par exemple, **A**) et le type de chaîne dans la structure de destination se trouve à droite (par exemple, **W**). Signifie LPSTR, **OLE** signifie LPOLESTR, **T** signifie LPTStr et **W** correspond à LPWStr.

Ainsi, DEVMODEA2W copie une `DEVMODE` structure avec des chaînes LPSTR dans `DEVMODE` une structure avec des chaînes LPWStr, TEXTMETRICOLE2T `TEXTMETRIC` copie une structure avec des chaînes `TEXTMETRIC` LPOLESTR dans une structure avec des chaînes LPTStr, et ainsi de suite.

Les deux chaînes converties `DEVMODE` dans la structure sont le nom`dmDeviceName`de l’appareil () et`dmFormName`le nom du formulaire (). Les `DEVMODE` macros de conversion de chaînes mettent également à jour`dmSize`la taille de la structure ().

Les quatre chaînes converties `TEXTMETRIC` dans la structure sont le premier`tmFirstChar`caractère (), le dernier`tmLastChar`caractère (), le caractère`tmDefaultChar`par défaut () et le caractère`tmBreakChar`de saut de ligne ().

Le comportement des macros `TEXTMETRIC` de conversion de `DEVMODE` chaînes et dépend de la directive de compilateur en vigueur, le cas échéant. Si les types source et de destination sont les mêmes, aucune conversion n'est effectuée. Les directives de compilateur changent **T** et **OLE** comme suit:

|Directive du compilateur appliquée|T devient|OLE devient|
|----------------------------------|---------------|-----------------|
|none|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|Unicode et **OLE2ANSI**  **\_**|**W**|**A**|

Le tableau suivant répertorie `DEVMODE` les `TEXTMETRIC` macros et les macros de conversion de chaînes.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
