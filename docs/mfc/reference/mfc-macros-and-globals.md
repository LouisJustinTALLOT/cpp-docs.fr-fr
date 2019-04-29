---
title: Macros et objet Globals MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
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
ms.openlocfilehash: 27664d4e48c0c4e09439f9e970ded9f2a630d90d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310269"
---
# <a name="mfc-macros-and-globals"></a>Macros et objet Globals MFC

La bibliothèque Microsoft Foundation Class peut être divisée en deux sections principales : (1) les classes MFC et les macros (2) et les variables globales. Si une fonction ou une variable n’est pas un membre d’une classe, il est une fonction globale ou une variable.

La bibliothèque MFC et la bibliothèque ATL (Active Template) partagent des macros de conversion de chaînes. Pour plus d’informations, consultez [Macros de Conversion de chaînes](../../atl/reference/string-conversion-macros.md) dans la documentation de ATL.

Les macros MFC et globals offrent des fonctionnalités dans les catégories suivantes.

## <a name="general-mfc"></a>Général MFC

- [Types de données](data-types-mfc.md)

- [Conversion de type des objets de classe MFC](type-casting-of-mfc-class-objects.md)

- [Services du modèle objet d’exécution](run-time-object-model-services.md)

- [Services de diagnostic](diagnostic-services.md)

- [Traitement des exceptions](exception-processing.md)

- [Mise en forme de CString et affichage de la boîte de message](cstring-formatting-and-message-box-display.md)

- [Tables des messages](message-map-macros-mfc.md)

- [Délégué et les tables d’Interface](delegate-and-interface-maps.md)

- [Modules et DLL](extension-dll-macros.md)

- [Gestion des informations et des applications](application-information-and-management.md)

- [ID de commande et de fenêtre standard](standard-command-and-window-ids.md)

- [Assistants de classe de collection](collection-class-helpers.md)

- [Fonctions d’image bitmap tramée et grise](gray-and-dithered-bitmap-functions.md)

- [Routines d’échange (DDX) de données de boîte de dialogue standard](standard-dialog-data-exchange-routines.md)

- [Routines de validation (DDV) de données de boîte de dialogue standard](standard-dialog-data-validation-routines.md)

- [AFX, messages](afx-messages.md)

- [Styles de contrôle ToolBar](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE, énumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Base de données

- [Fonctions de Field Exchange (RFX) d’enregistrement](record-field-exchange-functions.md) et [les fonctions RFX en bloc (RFX en bloc)](record-field-exchange-functions.md) pour les classes ODBC MFC

- [Fonctions d’exchange (DFX) champ d’enregistrement](record-field-exchange-functions.md) pour les classes DAO MFC

- [Fonctions d’échange de données de boîtes de dialogue (DDX) pour CRecordView et CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (classes DAO et ODBC MFC)

- [Fonctions d’exchange (DDX) de données de boîtes de dialogue pour contrôles OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Macros et objet globals pour vous aider à appeler directement les fonctions de la connectivité ODBC (Open Database) API](database-macros-and-globals.md)

- [Arrêt et l’initialisation du moteur de base de données DAO](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [URL Internet objet globals d’analyse](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / mappe les événements DHTML

- [Les macros d’assistance (DDX) d’échange de données de boîte de dialogue DHTML](ddx-dhtml-helper-macros.md)

- [DHTML, tables d’événements](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Initialisation d’OLE](ole-initialization.md)

- [Contrôle de l’application](application-control.md)

- [Tables de dispatch](dispatch-maps.md)

En outre, MFC fournit une fonction appelée [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) que permet de n’importe quel conteneur OLE développée avec MFC 4.0 pour prendre en charge incorporée de contrôles OLE.

## <a name="ole-controls"></a>Contrôles OLE

- [Constantes de type paramètre Variant](variant-parameter-type-constants.md)

- [Accès à la bibliothèque type](type-library-access.md)

- [Pages de propriétés](property-pages-mfc.md)

- [Tables d’événements](event-maps.md)

- [Tables de récepteurs d’événements](event-sink-maps.md)

- [Mappages de connexion](connection-maps.md)

- [Inscrire des contrôles OLE](registering-ole-controls.md)

- [Fabriques de classes et les licences](class-factories-and-licensing.md)

- [Persistance des contrôles OLE](persistence-of-ole-controls.md)

La première partie de cette section décrit chacune des catégories précédentes brièvement et répertorie les variables globales et les macros dans la catégorie, ainsi que de brèves descriptions de fonctionnalités. Suivant ce est des descriptions des fonctions globales, des variables globales, les macros dans la bibliothèque MFC.

> [!NOTE]
>  De nombreuses fonctions globales commencent par le préfixe « Afx », mais certains, par exemple, les boîte de dialogue (DDX) d’exchange et fonctions data de nombreuses fonctions de base de données, ne suivent pas cette convention. Toutes les variables globales commencent « afx » comme préfixe. Macros ne commencent pas par n’importe quel préfixe particulier, mais ils sont écrits en majuscules.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../mfc/class-library-overview.md)
