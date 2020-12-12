---
description: 'En savoir plus sur : contrôles ActiveX MFC : utilisation des pages de propriétés stock'
title: 'Contrôles ActiveX MFC : utilisation des pages de propriétés stock'
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 37cb6e5b5dfa08c5e7935064a66c2c77fe8dcde6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133053"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Contrôles ActiveX MFC : utilisation des pages de propriétés stock

Cet article décrit les pages de propriétés stock disponibles pour les contrôles ActiveX et comment les utiliser.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :

- [Contrôles ActiveX MFC : pages de propriétés](mfc-activex-controls-property-pages.md)

- [Contrôles ActiveX MFC : ajout d’une autre page de propriétés personnalisée](mfc-activex-controls-adding-another-custom-property-page.md)

MFC fournit trois pages de propriétés stock à utiliser avec les contrôles ActiveX : `CLSID_CColorPropPage` , `CLSID_CFontPropPage` et `CLSID_CPicturePropPage` . Ces pages affichent une interface utilisateur pour les propriétés de la couleur, de la police et de l’image de stock, respectivement.

Pour incorporer ces pages de propriétés dans un contrôle, ajoutez leurs ID au code qui initialise le tableau des ID de page de propriétés du contrôle. Dans l’exemple suivant, ce code, situé dans le fichier d’implémentation du contrôle (. CPP), initialise le tableau pour qu’il contienne les trois pages de propriétés stock et la page de propriétés par défaut (nommée `CMyPropPage` dans cet exemple) :

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Notez que le nombre de pages de propriétés, dans la macro BEGIN_PROPPAGEIDS, est 4. Cela représente le nombre de pages de propriétés prises en charge par le contrôle ActiveX.

Une fois ces modifications effectuées, régénérez votre projet. Votre contrôle comporte désormais des pages de propriétés pour les propriétés de police, d’image et de couleur.

> [!NOTE]
> Si les pages de propriétés stock du contrôle ne sont pas accessibles, cela peut être dû au fait que la DLL MFC (MFCxx.DLL) n’a pas été correctement inscrite auprès du système d’exploitation actuel. Cela résulte généralement de l’installation de Visual C++ sous un système d’exploitation différent de celui en cours d’exécution.

> [!TIP]
> Si vos pages de propriétés stock ne sont pas visibles (voir la remarque précédente), inscrivez la DLL en exécutant RegSvr32.exe à partir de la ligne de commande avec le nom de chemin d’accès complet à la DLL.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : ajout de propriétés stock](mfc-activex-controls-adding-stock-properties.md)
