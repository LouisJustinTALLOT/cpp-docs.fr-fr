---
title: CDialogImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09cc987b583bdddd78604f75bd07bc9e2743a1dc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206639"
---
# <a name="cdialogimpl-class"></a>CDialogImpl (classe)
Cette classe fournit des méthodes pour la création d’une boîte de dialogue modale ou non modale.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `CDialogImpl`.  
  
 *TBase*  
 La classe de base de votre nouvelle classe. La classe de base par défaut est [CWindow](../../atl/reference/cwindow-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Créer](#create)|Crée une boîte de dialogue non modale.|  
|[DestroyWindow](#destroywindow)|Détruit une boîte de dialogue non modale.|  
|[DoModal](#domodal)|Crée une boîte de dialogue modale.|  
|[EndDialog](#enddialog)|Détruit une boîte de dialogue modale.|  
  
### <a name="cdialogimplbaset-methods"></a>Méthodes CDialogImplBaseT  
  
|||  
|-|-|  
|[GetDialogProc](#getdialogproc)|Retourne la procédure de boîte de dialogue actuelle.|  
|[MapDialogRect](#mapdialogrect)|Mappe les unités de boîte de dialogue du rectangle spécifié pour les unités de l’écran (pixels).|  
|[OnFinalMessage](#onfinalmessage)|Appelé après réception du dernier message, généralement WM_NCDESTROY.|  
  
### <a name="static-functions"></a>Fonctions statiques  
  
|||  
|-|-|  
|[DialogProc](#dialogproc)|Traite les messages envoyés à la boîte de dialogue.|  
|[StartDialogProc](#startdialogproc)|Appelée lorsque le premier message est reçu pour traiter les messages envoyés à la boîte de dialogue.|  
  
## <a name="remarks"></a>Notes  
 Avec `CDialogImpl` vous pouvez créer une boîte de dialogue modale ou non modale. `CDialogImpl` Fournit la procédure de boîte de dialogue, qui utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.  
  
 Le destructeur de classe de base `~CWindowImplRoot` garantit que la fenêtre a disparu avant de détruire l’objet.  
  
 `CDialogImpl` dérive de `CDialogImplBaseT`, qui dérive à son tour de `CWindowImplRoot`.  
  
> [!NOTE]
>  Votre classe doit définir un `IDD` membre qui spécifie l’ID de ressource de modèle boîte de dialogue. Par exemple, l’Assistant Projet ATL ajoute automatiquement la ligne suivante à votre classe :  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 où `MyDlg` est la **nom court** entré dans l’Assistant **noms** page.  
  
|Pour plus d'informations sur|Voir|  
|--------------------------------|---------|  
|Création de contrôles|[Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md)|  
|À l’aide des boîtes de dialogue dans ATL|[ATL, classes de fenêtre](../../atl/atl-window-classes.md)|  
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|  
|Boîtes de dialogue|[Boîtes de dialogue](https://msdn.microsoft.com/library/windows/desktop/ms632588) et les rubriques suivantes dans le SDK Windows|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlwin.h  
  
##  <a name="create"></a>  CDialogImpl::Create  
 Crée une boîte de dialogue non modale.  
  
```  
HWND Create(
    HWND hWndParent,  
    LPARAM dwInitParam = NULL );  

HWND Create(
    HWND hWndParent,  
    RECT&, 
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>Paramètres  
 *hWndParent*  
 [in] Le handle vers la fenêtre propriétaire.  
  
 **RECT &** *rect*  
 [in] Un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui spécifie la taille et la position de la boîte de dialogue.  
  
 *dwInitParam*  
 [in] Spécifie la valeur à passer à la boîte de dialogue dans le *lParam* paramètre du message WM_INITDIALOG.  
  
### <a name="return-value"></a>Valeur de retour  
 Handle de la boîte de dialogue nouvellement créé.  
  
### <a name="remarks"></a>Notes  
 Cette boîte de dialogue est automatiquement joint à la `CDialogImpl` objet. Pour créer une boîte de dialogue modale, appelez [DoModal](#domodal). Le deuxième remplacement ci-dessus est utilisé uniquement avec [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow  
 Détruit une boîte de dialogue non modale.  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la boîte de dialogue a été détruite avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Retourne la valeur TRUE si la boîte de dialogue a été correctement détruite ; Sinon, FALSE.  
  
##  <a name="dialogproc"></a>  CDialogImpl::DialogProc  
 Cette fonction statique implémente la procédure de boîte de dialogue.  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>Paramètres  
 *hWnd*  
 [in] Handle de la boîte de dialogue.  
  
 *uMsg*  
 [in] Le message envoyé à la boîte de dialogue.  
  
 *wParam*  
 [in] Informations supplémentaires spécifiques au message.  
  
 *lParam*  
 [in] Informations supplémentaires spécifiques au message.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le message est traité ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 `DialogProc` utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.  
  
 Vous pouvez remplacer `DialogProc` pour fournir un mécanisme différent pour la gestion des messages.  
  
##  <a name="domodal"></a>  CDialogImpl::DoModal  
 Crée une boîte de dialogue modale.  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>Paramètres  
 *hWndParent*  
 [in] Le handle vers la fenêtre propriétaire. La valeur par défaut est la valeur de retour de la [GetActiveWindow](https://msdn.microsoft.com/library/windows/desktop/ms646292) fonction Win32.  
  
 *dwInitParam*  
 [in] Spécifie la valeur à passer à la boîte de dialogue dans le *lParam* paramètre du message WM_INITDIALOG.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, la valeur de la *nRetCode* paramètre spécifié dans l’appel à [EndDialog](#enddialog). Sinon, -1.  
  
### <a name="remarks"></a>Notes  
 Cette boîte de dialogue est automatiquement joint à la `CDialogImpl` objet.  
  
 Pour créer une boîte de dialogue non modale, appelez [créer](#create).  
  
##  <a name="enddialog"></a>  CDialogImpl::EndDialog  
 Détruit une boîte de dialogue modale.  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>Paramètres  
 *nRetCode*  
 [in] La valeur doit être retourné par [CDialogImpl::DoModal](#domodal).  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la boîte de dialogue est détruite ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 `EndDialog` doit être appelé via la procédure de boîte de dialogue. Une fois que la boîte de dialogue est détruite, Windows utilise la valeur de *nRetCode* comme valeur de retour pour `DoModal`, lequel créée de la boîte de dialogue.  
  
> [!NOTE]
>  N’appelez pas `EndDialog` pour détruire une boîte de dialogue non modale. Appelez [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) à la place.  
  
##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc  
 Retourne `DialogProc`, la procédure de boîte de dialogue actuelle.  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Procédure de boîte de dialogue actuelle.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour remplacer la procédure de boîte de dialogue par les vôtres.  
  
##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect  
 Convertit en unités (maps) les unités de boîte de dialogue du rectangle spécifié à l’écran (pixels).  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>Paramètres  
 *lpRect*  
 Pointe vers un `CRect` objet ou [RECT](../../mfc/reference/rect-structure1.md) structure qui doit recevoir les coordonnées clientes de la mise à jour qui englobe la région de mise à jour.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la mise à jour réussit ; 0 si la mise à jour échoue. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.  
  
### <a name="remarks"></a>Notes  
 La fonction remplace les coordonnées dans le texte spécifié `RECT` structure avec les coordonnées converties, ce qui permet la structure à utiliser pour créer une boîte de dialogue et positionner un contrôle dans une boîte de dialogue.  
  
##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage  
 Appelé après réception du dernier message (généralement `WM_NCDESTROY`).  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>Paramètres  
 *hWnd*  
 [in] Handle vers la fenêtre en cours de destruction.  
  
### <a name="remarks"></a>Notes  
 Notez que si vous souhaitez supprimer automatiquement votre objet lors de la destruction de la fenêtre, vous pouvez appeler **supprimer cela ;** ici.  
  
##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc  
 Appelée une seule fois, lorsque le premier message est reçu, pour traiter les messages envoyés à la boîte de dialogue.  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>Paramètres  
 *hWnd*  
 [in] Handle de la boîte de dialogue.  
  
 *uMsg*  
 [in] Le message envoyé à la boîte de dialogue.  
  
 *wParam*  
 [in] Informations supplémentaires spécifiques au message.  
  
 *lParam*  
 [in] Informations supplémentaires spécifiques au message.  
  
### <a name="return-value"></a>Valeur de retour  
 La procédure de fenêtre.  
  
### <a name="remarks"></a>Notes  
 Après l’appel initial à `StartDialogProc`, `DialogProc` est défini comme une procédure de la boîte de dialogue et les appels plus y accéder.  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)