---
description: 'En savoir plus sur : macros MFC et globales'
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
ms.openlocfilehash: 9e3d3acd74d1cf6db5856432cdefd632e36185f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219146"
---
# <a name="mfc-macros-and-globals"></a>Macros et objet Globals MFC

La bibliothèque MFC (Microsoft Foundation Class) peut être divisée en deux sections principales : (1) les classes MFC et (2) les macros et les éléments globaux. Si une fonction ou une variable n’est pas membre d’une classe, il s’agit d’une fonction ou d’une variable globale.

La bibliothèque MFC et la Active Template Library (ATL) partagent des macros de conversion de chaînes. Pour plus d’informations, consultez [macros de conversion de chaînes](../../atl/reference/string-conversion-macros.md) dans la documentation ATL.

Les macros et les globales MFC offrent les fonctionnalités dans les catégories suivantes.

## <a name="general-mfc"></a>MFC générales

- [Types de données](data-types-mfc.md)

- [Cast en type des objets de classe MFC](type-casting-of-mfc-class-objects.md)

- [Services du modèle objet au moment de l'exécution](run-time-object-model-services.md)

- [Services de diagnostic](diagnostic-services.md)

- [Traitement des exceptions](exception-processing.md)

- [Mise en forme de CString et affichage des boîtes de message](cstring-formatting-and-message-box-display.md)

- [Tables des messages](message-map-macros-mfc.md)

- [Mappages de délégués et d’interfaces](delegate-and-interface-maps.md)

- [Modules et DLL](extension-dll-macros.md)

- [Informations sur l'application et gestion](application-information-and-management.md)

- [ID de fenêtre et commande standard](standard-command-and-window-ids.md)

- [Assistances pour les classes de collection](collection-class-helpers.md)

- [Fonctions d’image bitmap tramée et grise](gray-and-dithered-bitmap-functions.md)

- [Routines d’échange de données de boîte de dialogue standard (DDX)](standard-dialog-data-exchange-routines.md)

- [Routines de validation de données de boîte de dialogue standard (DDV)](standard-dialog-data-validation-routines.md)

- [Messages AFX](afx-messages.md)

- [Styles de contrôle ToolBar](toolbar-control-styles.md)

- [CMFCImagePaintArea :: IMAGE_EDIT_MODE, énumération](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Base de données

- Fonctions [RFX (Record Field Exchange)](record-field-exchange-functions.md) et [échange de champs d’enregistrements en bloc (RFX en bloc)](record-field-exchange-functions.md) pour les classes ODBC MFC

- [Fonctions d’échange de champs d’enregistrement (DFX)](record-field-exchange-functions.md) pour les classes DAO MFC

- [Fonctions DDX (Dialog Data Exchange) pour CRecordView et CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (classes ODBC et DAO MFC)

- [Fonctions d’échange de données de boîtes de dialogue (DDX) pour les contrôles OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Macros et globales pour faciliter l’appel des fonctions de l’API Open Database Connectivity (ODBC) directement](database-macros-and-globals.md)

- [Initialisation et terminaison du moteur de base de données DAO](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Globals d'analyse des URL Internet](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>Mappages d’événements DHTML/DHTML

- [Macros d’assistance de l’échange de données de boîtes de dialogue (DDX) DHTML](ddx-dhtml-helper-macros.md)

- [Tables d'événements DHTML](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Initialisation d'OLE](ole-initialization.md)

- [Contrôle d'application](application-control.md)

- [Tables de dispatch](dispatch-maps.md)

En outre, MFC fournit une fonction appelée [AfxEnableControlContainer (](ole-initialization.md#afxenablecontrolcontainer) qui permet à n’importe quel conteneur OLE développé avec MFC 4,0 de prendre entièrement en charge les contrôles OLE incorporés.

## <a name="ole-controls"></a>Contrôles OLE

- [Constantes de type de paramètre de variante](variant-parameter-type-constants.md)

- [Accès à la bibliothèque de types](type-library-access.md)

- [Pages de propriétés](property-pages-mfc.md)

- [Tables d'événements](event-maps.md)

- [Tables de récepteurs d'événements](event-sink-maps.md)

- [Tables de connexions](connection-maps.md)

- [Inscription des contrôles OLE](registering-ole-controls.md)

- [Fabriques de classes et gestion des licences](class-factories-and-licensing.md)

- [Persistance des contrôles OLE](persistence-of-ole-controls.md)

La première partie de cette section décrit brièvement chacune des catégories précédentes et répertorie les variables globales et les macros dans la catégorie, ainsi que des descriptions succinctes des fonctionnalités. Voici une description des fonctions globales, des variables globales et des macros de la bibliothèque MFC.

> [!NOTE]
> De nombreuses fonctions globales commencent par le préfixe « AFX », mais certains, par exemple, les fonctions d’échange de données de boîtes de dialogue (DDX) et la plupart des fonctions de base de données, ne respectent pas cette Convention. Toutes les variables globales commencent par « AFX » en tant que préfixe. Les macros ne commencent pas par un préfixe particulier, mais elles sont écrites en lettres majuscules.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../mfc/class-library-overview.md)
