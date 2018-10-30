---
title: 'Contrôles ActiveX MFC : À l’aide Pages de propriétés Stock | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc7957e69821a409d5ad56bd10c222cbe85fbc54
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204403"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Contrôles ActiveX MFC : utilisation des pages de propriétés stock

Cet article décrit les pages de propriétés stock disponibles pour les contrôles ActiveX et comment les utiliser.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Pour plus d’informations sur l’utilisation des pages de propriétés dans un contrôle ActiveX, consultez les articles suivants :

- [Contrôles ActiveX MFC : pages de propriétés](../mfc/mfc-activex-controls-property-pages.md)

- [Contrôles ActiveX MFC : ajout d’une page de propriétés personnalisées](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC fournit trois pages de propriétés stock à utiliser avec des contrôles ActiveX : `CLSID_CColorPropPage`, `CLSID_CFontPropPage`, et `CLSID_CPicturePropPage`. Ces pages affichent une interface utilisateur pour le stock de couleurs, la police et propriétés de l’image, respectivement.

Pour incorporer ces pages de propriétés dans un contrôle, ajoutez leur ID pour le code qui initialise le tableau du contrôle de l’ID de page de propriété. Dans l’exemple suivant, ce code, situés dans le fichier d’implémentation (. (CPP), initialise le tableau destiné à contenir tous les trois pages de propriétés stock et la page de propriétés par défaut (nommée `CMyPropPage` dans cet exemple) :

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Notez que le nombre de pages de propriétés, dans la macro BEGIN_PROPPAGEIDS, est 4. Cela représente le nombre de pages de propriétés pris en charge par le contrôle ActiveX.

Après ont apporté ces modifications, régénérez votre projet. Votre contrôle a maintenant des pages de propriétés de la police, image et les propriétés de couleur.

> [!NOTE]
>  Si les pages de propriétés stock de contrôle n’est pas accessible, il peut être parce que la DLL MFC (MFCxx.DLL) n’a pas été correctement inscrit avec le système d’exploitation actuel. Cela se produit généralement à partir de l’installation de Visual C++ sous un système d’exploitation différent de celui en cours d’exécution.

> [!TIP]
>  Si vos pages de propriétés stock ne sont pas visibles (voir la remarque précédente), inscrivez la DLL en exécutant RegSvr32.exe à partir de la ligne de commande avec le nom de chemin d’accès complet à la DLL.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : ajout de propriétés stock](../mfc/mfc-activex-controls-adding-stock-properties.md)

