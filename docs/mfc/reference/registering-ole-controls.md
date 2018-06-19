---
title: Inscription des contrôles OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e51e4c425d3d16b57a2b1ce0d4fc2f585dc505d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378055"
---
# <a name="registering-ole-controls"></a>Inscription des contrôles OLE
Contrôles OLE, comme les autres objets de serveur OLE, est accessible par d’autres applications prenant en charge OLE. Pour cela, vous devez inscrire la bibliothèque de types et la classe du contrôle.  
  
 Les fonctions suivantes permettent d’ajouter et supprimer la classe du contrôle, de pages de propriétés et de bibliothèque de types dans la base de données d’inscription de Windows :  
  
### <a name="registering-ole-controls"></a>Inscription des contrôles OLE  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Ajoute la classe du contrôle à la base de données d’inscription.|  
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Ajoute une page de propriétés de contrôle à la base de données d’inscription.|  
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Ajoute la bibliothèque de types du contrôle à la base de données d’inscription.|  
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Supprime une classe de contrôle ou une classe de page de propriétés de la base de données d’inscription.|  
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Supprime la bibliothèque de types du contrôle à partir de la base de données d’inscription.|  
  
 `AfxOleRegisterTypeLib` est généralement appelée dans l’implémentation d’une DLL de contrôle de `DllRegisterServer`. De même, `AfxOleUnregisterTypeLib` est appelée par `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, et `AfxOleUnregisterClass` sont généralement appelées le `UpdateRegistry` fonction membre de la page de fabrication ou de la propriété de la classe d’un contrôle.  
  
##  <a name="afxoleregistercontrolclass"></a>  AfxOleRegisterControlClass  
 Inscrit la classe du contrôle avec la base de données d’inscription de Windows.  
  
```   
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,  
    REFCLSID clsid,  
    LPCTSTR pszProgID,  
    UINT idTypeName,  
    UINT idBitmap,  
    int nRegFlags,  
    DWORD dwMiscStatus,  
    REFGUID tlid,  
    WORD wVerMajor,  
    WORD wVerMinor); 
```  
  
### <a name="parameters"></a>Paramètres  
 `hInstance`  
 Le handle d’instance du module associé à la classe du contrôle.  
  
 `clsid`  
 L’ID de classe unique du contrôle.  
  
 `pszProgID`  
 ID de programme unique du contrôle.  
  
 `idTypeName`  
 L’ID de ressource de la chaîne qui contient un nom de type lisible par l’utilisateur pour le contrôle.  
  
 *idBitmap*  
 L’ID de ressource de l’image utilisée pour représenter le contrôle OLE dans une barre d’outils ou une palette.  
  
 `nRegFlags`  
 Contient un ou plusieurs des indicateurs suivants :  
  
- `afxRegInsertable` Permet le contrôle s’affiche dans la boîte de dialogue Insérer un objet pour les objets OLE.  
  
- `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = cloisonnement.  
  
- `afxRegFreeThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = libre.  
  
     Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = les deux. Consultez [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) dans le SDK Windows pour plus d’informations sur l’inscription du modèle de thread.  
  
> [!NOTE]
>  Dans les versions MFC avant 4.2 de MFC, la `int` `nRegFlags` paramètre était un **BOOL** paramètre, *bInsertable*, qui autorisée ou interdite le contrôle à insérer à partir de la boîte de dialogue Insérer un objet zone.  
  
 *dwMiscStatus*  
 Contient un ou plusieurs des indicateurs d’état suivants (pour obtenir une description des indicateurs, consultez **OLEMISC** énumération dans le SDK Windows) :  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 ID unique de la classe du contrôle.  
  
 `wVerMajor`  
 Numéro de version principale de la classe du contrôle.  
  
 `wVerMinor`  
 Numéro de version mineure de la classe du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la classe du contrôle a été inscrit ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Ainsi, le contrôle à utiliser par les conteneurs de contrôle OLE prenant en charge. `AfxOleRegisterControlClass` met à jour le Registre avec le nom du contrôle et l’emplacement sur le système et définit également le modèle de thread qui prend en charge par le contrôle dans le Registre. Pour plus d’informations, consultez [Technical Note 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), « Modèle de cloisonnement des threads dans OLE contrôles, » et [sur les processus et Threads](http://msdn.microsoft.com/library/windows/desktop/ms681917) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 L’exemple ci-dessus montre comment `AfxOleRegisterControlClass` est appelée avec l’indicateur pour insérer et l’indicateur de cloisonnement or pour créer le sixième paramètre de modèle :  
  
 [!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 Le contrôle s’afficheront dans la boîte de dialogue Insérer un objet pour les conteneurs activés, et il est compatible avec le modèle de cloisonnement. Les contrôles compatible avec le modèle de cloisonnement doivent vérifier que les données sont protégées par des verrous, de classe statique afin que lors d’un contrôle dans un cloisonnement accède à des données statiques, il n’est pas désactivé par le planificateur avant qu’il a terminé, et une autre instance de la même classe démarre à l’aide les mêmes données statiques. Tout accès aux données statiques sont entourées de code de section critique.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass  
 Inscrit la classe de page de propriétés avec la base de données d’inscription de Windows.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>Paramètres  
 `hInstance`  
 Le handle d’instance du module associé à la classe de page de propriétés.  
  
 `clsid`  
 ID de classe unique de la page de propriétés.  
  
 `idTypeName`  
 L’ID de ressource de la chaîne qui contient un nom lisible par l’utilisateur pour la page de propriétés.  
  
 `nRegFlags`  
 Peut contenir l’indicateur :  
  
- `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = cloisonnement.  
  
> [!NOTE]
>  Dans les versions MFC antérieures 4.2 de MFC, la `int` `nRegFlags` paramètre n’était pas disponible. Notez également que le `afxRegInsertable` indicateur n’est pas une option valide pour les pages de propriétés et entraîne une assertion dans MFC s’il est défini  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la classe du contrôle a été inscrit ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Ainsi, la page de propriétés à utiliser par les conteneurs de contrôle OLE prenant en charge. `AfxOleRegisterPropertyPageClass` met à jour le Registre avec le nom de la page de propriété et son emplacement sur le système et définit également le modèle de thread qui prend en charge par le contrôle dans le Registre. Pour plus d’informations, consultez [Technical Note 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), « Modèle de cloisonnement des threads dans OLE contrôles, » et [sur les processus et Threads](http://msdn.microsoft.com/library/windows/desktop/ms681917) dans le Kit de développement logiciel Windows.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib  
 Enregistre la bibliothèque de types avec la base de données d’inscription Windows et permet à la bibliothèque de types à utiliser par les autres conteneurs qui sont contrôle OLE prenant en charge.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>Paramètres  
 `hInstance`  
 Le handle d’instance de l’application associée à la bibliothèque de types.  
  
 *tlid*  
 ID unique de la bibliothèque de types.  
  
 *pszFileName*  
 Pointe vers le nom de fichier facultatif d’une bibliothèque de types localisée (. Fichiers TLB) pour le contrôle.  
  
 *pszHelpDir*  
 Le nom du répertoire où vous pouvez trouver le fichier d’aide pour la bibliothèque de types. Si **NULL**, le fichier d’aide est censé pour se trouver dans le même répertoire que la bibliothèque de types lui-même.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la bibliothèque de types a été inscrite ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction met à jour le Registre avec le nom de bibliothèque de type et son emplacement sur le système.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass  
 Supprime l’entrée de classe de page de contrôle ou la propriété de la base de données d’inscription de Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>Paramètres  
 *clsID*  
 L’ID de classe unique de la page de contrôle ou de propriété.  
  
 `pszProgID`  
 ID unique du programme de la page de contrôle ou de propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la classe de page de contrôle ou une propriété a été correctement annulée ; Sinon, 0.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib  
 Appelez cette fonction pour supprimer l’entrée de bibliothèque de type à partir de la base de données d’inscription de Windows.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>Paramètres  
 `tlID`  
 ID unique de la bibliothèque de types.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la bibliothèque de types a été correctement annulée ; Sinon, 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
