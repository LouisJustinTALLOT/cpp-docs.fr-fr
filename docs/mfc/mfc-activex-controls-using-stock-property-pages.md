---
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
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358191"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Contrôles ActiveX MFC : utilisation des pages de propriétés stock

Cet article traite des pages de propriété stock disponibles pour les contrôles ActiveX et comment les utiliser.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Pour plus d’informations sur l’utilisation des pages de propriété dans un contrôle ActiveX, voir les articles suivants:

- [Contrôles ActiveX MFC : pages de propriétés](../mfc/mfc-activex-controls-property-pages.md)

- [Contrôles ActiveX MFC : ajout d'une page de propriétés personnalisées](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC fournit trois pages de propriété stock `CLSID_CColorPropPage` `CLSID_CFontPropPage`pour `CLSID_CPicturePropPage`une utilisation avec les contrôles ActiveX: , , et . Ces pages affichent une interface utilisateur pour la couleur stock, la police et les propriétés d’image, respectivement.

Pour intégrer ces pages de propriété dans un contrôle, ajoutez leurs identifications au code qui initialise la gamme de services d’identification de la page de propriété du contrôle. Dans l’exemple suivant, ce code, situé dans le fichier d’implémentation de contrôle (. Le RPC) est en initialisation pour contenir les trois pages `CMyPropPage` de propriétés d’actions et la page de propriété par défaut (nommée dans cet exemple) :

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Notez que le nombre de pages de propriété, dans le BEGIN_PROPPAGEIDS macro, est de 4. Cela représente le nombre de pages de propriété prises en charge par le contrôle ActiveX.

Une fois ces modifications apportées, reconstruisez votre projet. Votre contrôle a maintenant des pages de propriété pour la police, l’image, et les propriétés de couleur.

> [!NOTE]
> Si les pages de propriété des stocks de contrôle ne peuvent pas être consultées, c’est peut-être parce que le MFC DLL (MFCxx.DLL) n’a pas été correctement enregistré auprès du système d’exploitation actuel. Cela résulte généralement de l’installation de Visual CMMD dans un système d’exploitation différent de celui actuellement en cours d’exécution.

> [!TIP]
> Si vos pages de propriété stock ne sont pas visibles (voir note précédente), enregistrez le DLL en exécutant RegSvr32.exe de la ligne de commande avec le nom complet du chemin à la DLL.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : ajout de propriétés stock](../mfc/mfc-activex-controls-adding-stock-properties.md)
