---
title: Contrôle d’application | Microsoft Docs
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
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 538a376dd14eae32864b494b7e79db1c89686b84
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315013"
---
# <a name="application-control"></a>Contrôle d'application
OLE nécessite un contrôle important sur les applications et leurs objets. Les DLL système OLE doivent être en mesure de lancer et de lancer automatiquement des applications, coordonner leur production et la modification d’objets, et ainsi de suite. Ces besoins dans les fonctions dans cette rubrique. Outre appelée par les DLL système OLE, ces fonctions doivent parfois être appelées par ainsi des applications. 
  
### <a name="application-control"></a>Contrôle d'application  
  
|||  
|-|-|  
|[AfxOleCanExitApp](#afxolecanexitapp)|Indique si l’application peut s’arrêter.|  
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Récupère le filtre de messages en cours de l’application.|  
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Récupère l’indicateur de contrôle de l’utilisateur actuel.|  
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Définit ou efface l’indicateur de contrôle de l’utilisateur.|  
|[AfxOleLockApp](#afxolelockapp)|Incrémente le nombre global de l’infrastructure du nombre d’objets actifs dans une application.|  
|[AfxOleLockControl](#afxolelockcontrol)| Verrouille la fabrique de classe du contrôle spécifié. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Décrémente décompte de l’infrastructure du nombre d’objets actifs dans une application.| 
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Déverrouille la fabrique de classe du contrôle spécifié. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Inscrit un serveur dans le Registre du système OLE.|  
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implémente l’interface utilisateur pour le *typename* commande de l’objet.|  

  
##  <a name="afxolecanexitapp"></a>  AfxOleCanExitApp  
 Indique si l’application peut s’arrêter.  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’application peut s’arrêter ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Une application ne doit pas s’arrêter s’il existe des références en suspens à ses objets. Les fonctions globales `AfxOleLockApp` et `AfxOleUnlockApp` incrémenter et décrémenter, respectivement, un compteur de références aux objets de l’application. L’application ne doit pas s’arrêter quand ce compteur est différent de zéro. Si le compteur est différente de zéro, fenêtre principale de l’application est masquée (pas détruite) lorsque l’utilisateur sélectionne Fermer dans le menu système ou quitter dans le menu fichier. L’infrastructure appelle cette fonction `CFrameWnd::OnClose`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>Configuration requise  
 **En-tête**: afxdisp.h 

##  <a name="afxolegetmessagefilter"></a>  AfxOleGetMessageFilter  
 Récupère le filtre de messages en cours de l’application.  
  
```   
COleMessageFilter* AFXAPI AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le filtre de messages en cours.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour accéder à des cours `COleMessageFilter`-dérivés d’objet, comme vous appelleriez `AfxGetApp` accéder à l’objet d’application actuel.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxwin.h 

##  <a name="afxolegetuserctrl"></a>  AfxOleGetUserCtrl  
 Récupère l’indicateur de contrôle de l’utilisateur actuel.  
  
```   
BOOL AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’utilisateur est dans le contrôle de l’application ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’utilisateur est dans le contrôle de l’application lorsque l’utilisateur a explicitement ouvert ou créé un nouveau document. L’utilisateur est également dans le contrôle si l’application n’a pas été lancée par le système OLE DLL — en d’autres termes, si l’utilisateur a lancé l’application avec l’interpréteur de commandes du système.  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  AfxOleSetUserCtrl  
 Définit ou efface l’indicateur de contrôle utilisateur, qui est expliquée dans la référence pour `AfxOleGetUserCtrl`.  
  
```  
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>Paramètres  
 *bUserCtrl*  
 Spécifie si l’indicateur de contrôle de l’utilisateur doit être configurée ou désactivée.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction lorsque l’utilisateur crée ou charge un document, mais pas lorsqu’un document est chargé ou créé via une action indirecte telles que le chargement d’un objet incorporé à partir d’une application de conteneur.  
  
 Appelez cette fonction si d’autres actions dans votre application doivent placer l’utilisateur dans le contrôle de l’application.  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp  
 Incrémente le nombre global de l’infrastructure du nombre d’objets actifs dans l’application.  
  
```   
void AFXAPI AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>Notes  
 Le framework conserve un décompte du nombre d’objets actifs dans une application. Le `AfxOleLockApp` et `AfxOleUnlockApp` fonctions, respectivement, incrémenter et décrémenter ce nombre.  
  
 Lorsque l’utilisateur tente de fermer une application qui contient des objets actives, une application pour laquelle le nombre d’objets actifs est différent de zéro, le framework masque l’application à partir de la vue de l’utilisateur au lieu d’arrêter complètement. Le `AfxOleCanExitApp` fonction indique si l’application peut s’arrêter.  
  
 Appelez `AfxOleLockApp` à partir de n’importe quel objet qui expose les interfaces OLE, s’il serait pas souhaitable pour cet objet à détruire tout toujours utilisé par une application cliente. Également appeler `AfxOleUnlockApp` dans le destructeur de n’importe quel objet qui appelle `AfxOleLockApp` dans le constructeur. Par défaut, `COleDocument` (et les classes dérivées) automatiquement verrouiller et déverrouiller l’application.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  AfxOleUnlockApp  
 Décrémente count de l’infrastructure d’objets actifs dans l’application.  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>Notes  
 Consultez `AfxOleLockApp` pour plus d’informations.  
  
 Lorsque le nombre d’objets actifs atteint zéro, `AfxOleOnReleaseAllObjects` est appelée.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [AfxOleLockApp](#afxolelockapp).  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxdisp.h  

 ## <a name="afxolelockcontrol"></a>AfxOleLockControl
Verrouille la fabrique de classe du contrôle spécifié afin que créées dynamiquement des données associées au contrôle restent en mémoire.  
   
### <a name="syntax"></a>Syntaxe    
```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );  
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>Paramètres  
 *clsid*  
 L’ID de classe unique du contrôle.  
  
 *lpszProgID*  
 L’ID unique du programme du contrôle.  
   
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fabrique de classe du contrôle a été verrouillée avec succès ; sinon 0.  
   
### <a name="remarks"></a>Notes  
 Cela peut considérablement accélérer l’affichage des contrôles. Par exemple, une fois vous créer un contrôle dans une boîte de dialogue et verrouiller le contrôle avec `AfxOleLockControl`, vous n’avez pas besoin de créer et de supprimer chaque fois que la boîte de dialogue est affichée ou détruit. Si l’utilisateur ouvre et ferme une boîte de dialogue à plusieurs reprises, verrouillage de vos contrôles peut améliorer considérablement les performances. Lorsque vous êtes prêt à détruire le contrôle, appelez `AfxOleUnlockControl`.  
   
### <a name="example"></a>Exemple  
```cpp
// Starts and locks control's (Microsoft Calendar) class factory. 
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AfxOleUnlockControl](#afxoleunlockcontrol)
 
##  <a name="afxoleregisterserverclass"></a>  AfxOleRegisterServerClass  
 Cette fonction permet d’inscrire votre serveur dans le Registre du système OLE.  
  
```   
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszShortTypeName,  
    LPCTSTR lpszLongTypeName,  
    OLE_APPTYPE nAppType = OAT_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL); 
```  
  
### <a name="parameters"></a>Paramètres  
 *clsid*  
 Référence à l’ID de classe OLE. du serveur  
  
 *lpszClassName*  
 Pointeur vers une chaîne contenant le nom de classe des objets du serveur.  
  
 *lpszShortTypeName*  
 Pointeur vers une chaîne contenant le nom court du type d’objet du serveur, telles que « Graphique ».  
  
 *lpszLongTypeName*  
 Pointeur vers une chaîne contenant le nom long du type d’objet du serveur, telles que « Graphique de Microsoft Excel 5.0 ».  
  
 *nAppType*  
 Valeur issue de l’énumération OLE_APPTYPE, en spécifiant le type d’application OLE. Les valeurs possibles sont les suivantes :  
  
- OAT_INPLACE_SERVER serveur a l’interface utilisateur complète du serveur.  
  
- OAT_SERVER Server prend en charge uniquement l’incorporation.  
  
- OAT_CONTAINER conteneur prend en charge les liaisons aux incorporations.  
  
- OAT_DISPATCH_OBJECT `IDispatch`-objet compatible.  
  
 *rglpszRegister*  
 Tableau de pointeurs vers des chaînes représentant les clés et valeurs à ajouter au Registre système OLE si aucune valeur existante pour les clés ne se trouvent.  
  
 *rglpszOverwrite*  
 Tableau de pointeurs vers des chaînes représentant les clés et valeurs à ajouter au Registre système OLE si le Registre contient des valeurs existantes pour les clés donnés.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la classe de serveur est inscrit avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 La plupart des applications peuvent utiliser `COleTemplateServer::Register` pour inscrire des types de documents de l’application. Si le format de Registre du système de votre application ne tient pas le modèle par défaut, vous pouvez utiliser `AfxOleRegisterServerClass` pour plus de contrôle.  
  
 Le Registre se compose d’un jeu de clés et valeurs. Le *rglpszRegister* et *rglpszOverwrite* arguments sont des tableaux de pointeurs vers des chaînes, chacune se compose d’une clé et une valeur séparés par un **NULL** caractère ( `'\0'`). Chacune de ces chaînes peut avoir des paramètres remplaçables dont les emplacements sont marquées par les séquences de caractères *%1* via *%5*.  
  
 Les symboles sont renseignés comme suit :  
  
|Symbole|Value|  
|------------|-----------|  
|%1|ID de classe, sous formaté de chaîne|  
|%2|Nom de classe|  
|%3|Chemin d’accès au fichier exécutable|  
|%4|Nom de type court|  
|%5|Nom de type long|  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  AfxOleSetEditMenu  
 Implémente l’interface utilisateur pour le *typename* commande de l’objet.  
  
```   
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>Paramètres  
 *pClient*  
 Pointeur vers l’élément OLE de client.  
  
 *pMenu*  
 Un pointeur vers l’objet de menu à mettre à jour.  
  
 *iMenuItem*  
 Index de l’élément de menu à mettre à jour.  
  
 *nIDVerbMin*  
 L’ID de commande qui correspond au verbe principal.  
  
 *nIDVerbMax*  
 L’ID de commande qui correspond au dernier verbe.  
  
 *nIDConvert*  
 ID de l’élément de menu Convert.  
  
### <a name="remarks"></a>Notes  
 Si le serveur reconnaît uniquement un primary (verbe), l’élément de menu devienne « verbe *typename* objet » et le *nIDVerbMin* commande est envoyée lorsque l’utilisateur sélectionne la commande. Si le serveur reconnaît plusieurs verbes, l’élément de menu devienne « *typename* objet » et un sous-menu répertoriant tous les verbes s’affiche lorsque l’utilisateur sélectionne la commande. Lorsque l’utilisateur choisit un verbe dans le sous-menu, *nIDVerbMin* est envoyé si la première action est choisie, *nIDVerbMin* + 1 est envoyé si la deuxième action est sélectionné et ainsi de suite. La valeur par défaut `COleDocument` implémentation gère automatiquement cette fonctionnalité.  
  
 Vous devez disposer de l’instruction suivante dans le script de ressources d’application de votre client (. Fichier RC) :  
  
 **#include \<afxolecl.rc >**  

### <a name="requirements"></a>Configuration requise  
 **En-tête**: afxole.h 

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="afxoleunlockcontrol"></a> AfxOleUnlockControl
Déverrouille la fabrique de classe du contrôle spécifié.  
   
### <a name="syntax"></a>Syntaxe  
```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );  
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>Paramètres  
 *clsid*  
 L’ID de classe unique du contrôle.  
  
 *lpszProgID*  
 L’ID unique du programme du contrôle.  
   
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fabrique de classe du contrôle a été correctement déverrouillée ; sinon 0.  
   
### <a name="remarks"></a>Notes  
 Un contrôle est verrouillé avec `AfxOleLockControl`, de sorte que créées dynamiquement des données associées au contrôle restent en mémoire. Cela peut considérablement accélérer l’affichage du contrôle, car le contrôle ne doive pas être créé et détruit chaque fois qu’il est affiché. Lorsque vous êtes prêt à détruire le contrôle, appelez `AfxOleUnlockControl`.  
   
### <a name="example"></a>Exemple  
```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));

```
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)  
 [AfxOleLockControl](#afxolelockcontrol)

