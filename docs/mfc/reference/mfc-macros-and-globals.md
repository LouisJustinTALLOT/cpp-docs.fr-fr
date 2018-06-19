---
title: MFC Macros and Globals | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 189e3f272d679030c11fcd11ca4760f59944faeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375684"
---
# <a name="mfc-macros-and-globals"></a>Macros et objet Globals MFC
La bibliothèque Microsoft Foundation Class peut être divisée en deux sections principales : (1) le classes MFC et les macros (2) et les variables globales. Si une fonction ou une variable n’est pas un membre d’une classe, il est une fonction globale ou une variable.  
  
 La bibliothèque MFC et la bibliothèque ATL (Active Template) partagent des macros de conversion de chaînes. Pour plus d’informations, consultez [Macros de Conversion de chaînes](../../atl/reference/string-conversion-macros.md) dans la documentation ATL.  
  
 Les macros MFC et objet globals offrent des fonctionnalités dans les catégories suivantes.  
  
## <a name="general-mfc"></a>Général MFC  
  
-   [Types de données](data-types-mfc.md)  
  
-   [Conversion de type des objets de classe MFC](type-casting-of-mfc-class-objects.md)  
  
-   [Services du modèle objet d’exécution](run-time-object-model-services.md)  
  
-   [Services de diagnostic](diagnostic-services.md)  
  
-   [Traitement des exceptions](exception-processing.md)  
  
-   [Mise en forme de CString et affichage de la boîte de message](cstring-formatting-and-message-box-display.md)  
  
-   [Tables des messages](message-map-macros-mfc.md)  

-   [Délégué et les tables d’Interface](delegate-and-interface-maps.md)

-   [Modules et DLL](extension-dll-macros.md)
  
-   [Gestion des informations et des applications](application-information-and-management.md)  
  
-   [ID de commande et de fenêtre standard](standard-command-and-window-ids.md)  
  
-   [Assistants de classe de collection](collection-class-helpers.md)  
  
-   [Fonctions d’image bitmap tramée et grise](gray-and-dithered-bitmap-functions.md)  
  
-   [Routines d’échange (DDX) de données de boîte de dialogue standard](standard-dialog-data-exchange-routines.md)  
  
-   [Routines de validation (DDV) de données de boîte de dialogue standard](standard-dialog-data-validation-routines.md)  
  
-   [AFX, messages](afx-messages.md)  
  
-   [Styles de contrôle ToolBar](toolbar-control-styles.md)  
  
-   [CMFCImagePaintArea::IMAGE_EDIT_MODE, énumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>Base de données  
  
-   [Enregistrer les fonctions Field Exchange (RFX)](record-field-exchange-functions.md) et [les fonctions RFX en bloc (RFX en bloc)](record-field-exchange-functions.md) pour les classes ODBC MFC  
  
-   [Enregistrer les fonctions d’échange (DFX) champ](record-field-exchange-functions.md) pour les classes DAO MFC  
  
-   [Fonctions d’échange de données de boîtes de dialogue (DDX) pour CRecordView et CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (classes DAO et ODBC MFC)  
  
-   [Fonctions d’exchange (DDX) de données de boîtes de dialogue pour contrôles OLE](dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [Macros et objet globals pour aider à l’appel direct de fonctions de base de données ODBC (Open Connectivity) API](database-macros-and-globals.md)  
  
-   [Arrêt et l’initialisation du moteur de base de données DAO](dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>Internet  
  
-   [URL Internet objet globals d’analyse](internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>DHTML / événement DHTML est mappé.  
  
-   [Les macros d’assistance (DDX) d’échange de données de boîte de dialogue DHTML](ddx-dhtml-helper-macros.md)  
  
-   [DHTML, tables d’événements](dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [Initialisation d’OLE](ole-initialization.md)  
  
-   [Contrôle d’application](application-control.md)  
  
-   [Tables de dispatch](dispatch-maps.md)  
  
 En outre, MFC fournit une fonction appelée [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) que permet de n’importe quel conteneur OLE développé avec MFC 4.0 pour prendre entièrement en charge incorporée des contrôles OLE.  
  
## <a name="ole-controls"></a>Contrôles OLE  
  
-   [Constantes de type paramètre Variant](variant-parameter-type-constants.md)  
  
-   [Accès de bibliothèque de type](type-library-access.md)  
  
-   [Pages de propriétés](property-pages-mfc.md)  
  
-   [Tables d’événements](event-maps.md)  
  
-   [Tables de récepteurs d’événements](event-sink-maps.md)  
  
-   [Mappages de connexion](connection-maps.md)  
  
-   [Inscrire des contrôles OLE](registering-ole-controls.md)  
  
-   [Fabriques de classes et les licences](class-factories-and-licensing.md)  
  
-   [Persistance des contrôles OLE](persistence-of-ole-controls.md)  
  
 La première partie de cette section décrit chacune des catégories précédentes brièvement et répertorie les variables globales et les macros dans la catégorie, ainsi que de brèves descriptions de fonctionnalités. Ce sont des descriptions des fonctions globales, les variables globales et les macros dans la bibliothèque MFC.  
  
> [!NOTE]
>  De nombreuses fonctions globales commencent par le préfixe « Afx », mais certaines, par exemple, les fonctions d’échange de données boîte de dialogue et la plupart des fonctions de la base de données, ne suivent pas cette convention. Toutes les variables globales commencent par « afx » comme préfixe. Les macros ne commencent pas par n’importe quel préfixe particulier, mais ils sont écrits en majuscules.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../mfc/class-library-overview.md)



