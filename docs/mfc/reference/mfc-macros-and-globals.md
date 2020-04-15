---
title: Macros et objet Globals MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373044"
---
# <a name="mfc-macros-and-globals"></a>Macros et objet Globals MFC

La Bibliothèque de classe microsoft Foundation peut être divisée en deux sections principales : (1) les classes MFC et (2) macros et globals. Si une fonction ou une variable n’est pas membre d’une classe, il s’agit d’une fonction globale ou variable.

La bibliothèque MFC et la Bibliothèque Active Template (ATL) partagent des macros de conversion des chaînes. Pour plus d’informations, voir [Macro de conversion des cordes](../../atl/reference/string-conversion-macros.md) dans la documentation ATL.

Les macros et les globals MFC offrent des fonctionnalités dans les catégories suivantes.

## <a name="general-mfc"></a>Général MFC

- [Types de données](data-types-mfc.md)

- [Type de moulage d’objets de classe MFC](type-casting-of-mfc-class-objects.md)

- [Services de modèle d’objets à durée de couru](run-time-object-model-services.md)

- [Services de diagnostic](diagnostic-services.md)

- [Traitement des exceptions](exception-processing.md)

- [Formatage CString et affichage de boîte de message](cstring-formatting-and-message-box-display.md)

- [Cartes de messages](message-map-macros-mfc.md)

- [Cartes des délégués et des interfaces](delegate-and-interface-maps.md)

- [Modules et DLL](extension-dll-macros.md)

- [Informations et gestion des applications](application-information-and-management.md)

- [Œd de commande et de fenêtre standard](standard-command-and-window-ids.md)

- [Aides de classe de collection](collection-class-helpers.md)

- [Fonctions de bitmap gris et tergiversés](gray-and-dithered-bitmap-functions.md)

- [Routines d’échange de données de dialogue standard (DDX)](standard-dialog-data-exchange-routines.md)

- [Routines standard de validation des données de dialogue (DDV)](standard-dialog-data-validation-routines.md)

- [AFX, messages](afx-messages.md)

- [Styles de contrôle ToolBar](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Base de données

- [Fonctions Record Field Exchange (RFX)](record-field-exchange-functions.md) et [Bulk Record Field Exchange (bulk RFX) fonctions](record-field-exchange-functions.md) pour les classes MFC ODBC

- [Fonctions d’échange de terrain record (DFX)](record-field-exchange-functions.md) pour les classes MFC DAO

- [Fonctions d’échange de données de dialogue (DDX) pour les classes CRecordView et CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (MFC ODBC et DAO)

- [Fonctions d’échange de données de dialogue (DDX) pour les contrôles OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Macros et mondiaux pour aider à appeler Open Database Connectivity (ODBC) fonctions API directement](database-macros-and-globals.md)

- [Initialisation et terminaison du moteur de base de données DAO](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Globals d'analyse des URL Internet](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML Event Maps

- [DHTML dialog data exchange (DDX) macros d’aide](ddx-dhtml-helper-macros.md)

- [Cartes d’événements DHTML](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Initialisation OLE](ole-initialization.md)

- [Contrôle des applications](application-control.md)

- [Cartes d’expédition](dispatch-maps.md)

En outre, MFC fournit une fonction appelée [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) qui permet à tout conteneur OLE développé avec MFC 4.0 de prendre pleinement en charge les contrôles OLE intégrés.

## <a name="ole-controls"></a>Contrôles OLE

- [Variation de type de paramètre constantes](variant-parameter-type-constants.md)

- [Accès à la bibliothèque de type](type-library-access.md)

- [Pages de propriété](property-pages-mfc.md)

- [Tables d'événements](event-maps.md)

- [Cartes d’évier d’événement](event-sink-maps.md)

- [Cartes de connexion](connection-maps.md)

- [Enregistrement des contrôles OLE](registering-ole-controls.md)

- [Fabriques de classes et gestion des licences](class-factories-and-licensing.md)

- [Persistance des contrôles OLE](persistence-of-ole-controls.md)

La première partie de cette section traite brièvement de chacune des catégories précédentes et répertorie les globaux et les macros de la catégorie, ainsi que de brèves descriptions de fonctionnalités. Il s’agit ensuite de descriptions des fonctions globales, des variables globales et des macros de la bibliothèque MFC.

> [!NOTE]
> De nombreuses fonctions globales commencent par le préfixe "Afx", mais certains, par exemple, les fonctions d’échange de données de dialogue (DDX) et de nombreuses fonctions de base de données, ne suivent pas cette convention. Toutes les variables globales commencent par "afx" comme préfixe. Les macros ne commencent pas par un préfixe particulier, mais ils sont écrits en lettres majuscules.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../mfc/class-library-overview.md)
