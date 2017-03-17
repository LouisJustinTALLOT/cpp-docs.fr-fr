---
title: Classe de CAxDialogImpl | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
dev_langs:
- C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 71e77ac6b8d2a89e384817020772bb855ce2d573
ms.lasthandoff: 02/24/2017

---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl (classe)
Cette classe implémente une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `CAxDialogImpl`.  
  
 *TBase*  
 La classe de fenêtre de base de **CDialogImplBaseT**.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Appelez cette méthode pour conseiller ou déconseiller toutes les entrées de la table d’événements de l’objet récepteur carte.|  
|[CAxDialogImpl::Create](#create)|Appelez cette méthode pour créer une boîte de dialogue non modale.|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Appelez cette méthode pour détruire une boîte de dialogue non modale.|  
|[CAxDialogImpl::DoModal](#domodal)|Appelez cette méthode pour créer une boîte de dialogue modale.|  
|[CAxDialogImpl::EndDialog](#enddialog)|Appelez cette méthode pour détruire une boîte de dialogue modale.|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Appelez cette méthode pour obtenir un pointeur vers le `DialogProc` fonction de rappel.|  
|[CAxDialogImpl::GetIDD](#getidd)|Appelez cette méthode pour obtenir l’ID de ressource de modèle de boîte de dialogue|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Appelez cette méthode pour déterminer si un message est destiné à cette boîte de dialogue et, dans le cas, traiter le message.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|Une variable qui existe uniquement en mode de débogage génère et est défini sur true si la boîte de dialogue est modale.|  
  
## <a name="remarks"></a>Remarques  
 `CAxDialogImpl`vous permet de créer une boîte de dialogue modale ou non modale. `CAxDialogImpl`Fournit la procédure de boîte de dialogue, qui utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.  
  
 `CAxDialogImpl`dérive de `CDialogImplBaseT`, qui dérive à son tour de *TBase* (par défaut, `CWindow`) et `CMessageMap`.  
  
 Votre classe doit définir un membre IDD qui spécifie l’ID de ressource boîte de dialogue Modèles. Par exemple, ajoutez un objet de boîte de dialogue ATL à l’aide de la **ajouter une classe** boîte de dialogue ajoute automatiquement la ligne suivante à votre classe :  
  
 [!code-cpp[# NVC_ATL_Windowing&41;](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 où `MyDialog` est la **nom court** entré dans l’Assistant dialogue ATL.  
  
 Consultez la page [l’implémentation d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) pour plus d’informations.  
  
 Notez qu’un contrôle ActiveX dans une boîte de dialogue modale créé avec `CAxDialogImpl` ne prendra pas en charge des touches accélérateur. Pour prendre en charge des touches d’accès rapide sur une boîte de dialogue créée avec `CAxDialogImpl`, créer une boîte de dialogue non modale et, à l’aide de votre propre boucle de messages, utilisez [CAxDialogImpl::IsDialogMessage](#isdialogmessage) après avoir obtenu un message de la file d’attente pour gérer une touche accélérateur.  
  
 Pour plus d’informations sur `CAxDialogImpl`, consultez [Forum aux questions de relation contenant-contenu de contrôle ATL](../../atl/atl-control-containment-faq.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlwin.h  
  
##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap  
 Appelez cette méthode pour conseiller ou déconseiller toutes les entrées de la table d’événements de l’objet récepteur carte.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Paramètres  
 `bAdvise`  
 La valeur true si toutes les entrées de récepteur sont d’être informé ; récepteur False si toutes les entrées doivent être cessent d’être averties.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="create"></a>CAxDialogImpl::Create  
 Appelez cette méthode pour créer une boîte de dialogue non modale.  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 [in] Handle de la fenêtre propriétaire.  
  
 `dwInitParam`  
 [in] Spécifie la valeur à passer à la boîte de dialogue dans le `lParam` paramètre de la **WM_INITDIALOG** message.  
  
 **RECT SE**  
 Ce paramètre n'est pas utilisé. Ce paramètre est passé en `CComControl`.  
  
### <a name="return-value"></a>Valeur de retour  
 Handle de la boîte de dialogue qui vient d’être créé.  
  
### <a name="remarks"></a>Remarques  
 Cette boîte de dialogue est automatiquement joint à la `CAxDialogImpl` objet. Pour créer une boîte de dialogue modale, appelez [DoModal](#domodal).  
  
 Le remplacement du deuxième est fourni uniquement pour les boîtes de dialogue peuvent être utilisées avec [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>CAxDialogImpl::DestroyWindow  
 Appelez cette méthode pour détruire une boîte de dialogue non modale.  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la fenêtre est détruite avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Remarques  
 N’appelez pas `DestroyWindow` de suppression de la boîte de dialogue modale. Appelez [EndDialog](#enddialog) à la place.  
  
##  <a name="domodal"></a>CAxDialogImpl::DoModal  
 Appelez cette méthode pour créer une boîte de dialogue modale.  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 [in] Handle de la fenêtre propriétaire. La valeur par défaut est la valeur de retour de la [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) fonction Win32.  
  
 `dwInitParam`  
 [in] Spécifie la valeur à passer à la boîte de dialogue dans le `lParam` paramètre de la **WM_INITDIALOG** message.  
  
### <a name="return-value"></a>Valeur de retour  
 Si l’opération réussit, la valeur de la `nRetCode` paramètre spécifié dans l’appel à [EndDialog](#enddialog); sinon, -1.  
  
### <a name="remarks"></a>Remarques  
 Cette boîte de dialogue est automatiquement joint à la `CAxDialogImpl` objet.  
  
 Pour créer une boîte de dialogue non modale, appelez [créer](#create).  
  
##  <a name="enddialog"></a>CAxDialogImpl::EndDialog  
 Appelez cette méthode pour détruire une boîte de dialogue modale.  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>Paramètres  
 `nRetCode`  
 [in] La valeur à retourner par [DoModal](#domodal).  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la boîte de dialogue est détruite ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 `EndDialog`doit être appelé via la procédure de boîte de dialogue. Une fois la boîte de dialogue est détruite, Windows utilise la valeur de `nRetCode` comme valeur de retour pour `DoModal`, qui créé la boîte de dialogue.  
  
> [!NOTE]
>  N’appelez pas `EndDialog` pour détruire une boîte de dialogue non modale. Appelez [DestroyWindow](#destroywindow) à la place.  
  
##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc  
 Appelez cette méthode pour obtenir un pointeur vers le `DialogProc` fonction de rappel.  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le `DialogProc` fonction de rappel.  
  
### <a name="remarks"></a>Remarques  
 Le `DialogProc` fonction est une fonction de rappel définie par l’application.  
  
##  <a name="getidd"></a>CAxDialogImpl::GetIDD  
 Appelez cette méthode pour obtenir l’ID de ressource boîte de dialogue Modèles.  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’ID de ressource boîte de dialogue Modèles.  
  
##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage  
 Appelez cette méthode pour déterminer si un message est destiné à cette boîte de dialogue et, dans le cas, traiter le message.  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 `pMsg`  
 Pointeur vers un [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) structure qui contient le message à vérifier.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si le message a été traité, FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode est destinée à être appelée à partir d’une boucle de message.  
  
##  <a name="m_bmodal"></a>CAxDialogImpl::m_bModal  
 Une variable qui existe uniquement en mode de débogage génère et est défini sur true si la boîte de dialogue est modale.  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>Voir aussi  
 [CDialogImpl (classe)](../../atl/reference/cdialogimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

