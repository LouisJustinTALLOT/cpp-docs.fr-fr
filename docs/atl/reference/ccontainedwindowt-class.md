---
title: Classe de CContainedWindowT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f3f90e23eed3bd1eba80bbf90fe73de45eb7cfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366482"
---
# <a name="ccontainedwindowt-class"></a>Classe de CContainedWindowT
Cette classe implémente une fenêtre contenue dans un autre objet.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class CContainedWindowT : public TBase
```  
  
#### <a name="parameters"></a>Paramètres  
 *TBase*  
 La classe de base de votre nouvelle classe. La classe de base par défaut est `CWindow`.  
  
 `TWinTraits`  
 Une classe de traits qui définit les styles de votre fenêtre. La valeur par défaut est `CControlWinTraits`.  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) est une spécialisation de `CContainedWindowT`. Si vous souhaitez modifier la classe de base ou les caractéristiques, utilisez `CContainedWindowT` directement.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Constructeur. Initialise les membres de données pour spécifier le mappage de message pour traiter les messages de la fenêtre de la relation contenant-contenu.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CContainedWindowT::Create](#create)|Crée une fenêtre.|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Fournit le traitement du message par défaut.|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Retourne le message actuel.|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Inscrit la classe de fenêtre de la fenêtre contenue.|  
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Sous-classe une fenêtre.|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Modifie le mappage de message qui est utilisé pour traiter les messages de la fenêtre de la relation contenant-contenu.|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaure une fenêtre précédemment sous-classée.|  
|[CContainedWindowT::WindowProc](#windowproc)|(Statique) Traite les messages envoyés à la fenêtre de relation contenant-contenue.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identifie la table des messages pour traiter les messages de la fenêtre de la relation contenant-contenu.|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Spécifie le nom d’une classe de fenêtre existante sur laquelle une nouvelle classe de fenêtre doit être basée.|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Pointe vers la procédure de fenêtre d'origine de la classe de fenêtre.|  
|[CContainedWindowT::m_pObject](#m_pobject)|Pointe vers l’objet conteneur.|  
  
## <a name="remarks"></a>Notes  
 `CContainedWindowT` implémente une fenêtre contenue dans un autre objet. `CContainedWindowT`'s utilise de procédure de fenêtre un message de mappage dans l’objet conteneur pour diriger les messages pour les gestionnaires appropriés. Lorsque vous construisez un `CContainedWindowT` de l’objet, vous spécifiez quelle table des messages doit être utilisé.  
  
 `CContainedWindowT` vous permet de créer une nouvelle fenêtre par surclasser une classe de fenêtre existante. Le **créer** méthode enregistre tout d’abord une classe de fenêtre qui est basée sur une classe existante mais utilise `CContainedWindowT::WindowProc`. **Créer** crée ensuite une fenêtre basée sur cette nouvelle classe de fenêtre. Chaque instance de `CContainedWindowT` pouvez superclasse une classe de fenêtre différente.  
  
 `CContainedWindowT` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CContainedWindowT` et remplace la procédure de fenêtre par `CContainedWindowT::WindowProc`. Chaque instance de `CContainedWindowT` peut sous-classer une fenêtre différente.  
  
> [!NOTE]
>  Pour toute donnée `CContainedWindowT` de l’objet, appelez **créer** ou `SubclassWindow`. Vous ne devez pas appeler les deux méthodes sur le même objet.  
  
 Lorsque vous utilisez la **ajouter un contrôle basé sur** option dans l’Assistant Projet ATL, l’Assistant ajoute automatiquement un `CContainedWindowT` membre de données à la classe implémentant le contrôle. L’exemple suivant montre comment la fenêtre contenue est déclarée :  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
|Pour plus d'informations sur|Voir|  
|--------------------------------|---------|  
|Création de contrôles|[Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Utilisation de fenêtres dans ATL|[ATL, classes de fenêtre](../../atl/atl-window-classes.md)|  
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|  
|Windows|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595) et les rubriques suivantes dans le SDK Windows|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `TBase`  
  
 `CContainedWindowT`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlwin.h  
  
##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT  
 Le constructeur initialise les membres de données.  
  
```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```     
  
### <a name="parameters"></a>Paramètres  
 `lpszClassName`  
 [in] Le nom d’une classe de fenêtre existante sur laquelle repose la fenêtre contenue.  
  
 `pObject`  
 [in] Pointeur vers l’objet conteneur qui déclare la table des messages. Cette classe de l’objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] Identifie la table des messages qui traitera les messages de la fenêtre de la relation contenant-contenu. La valeur par défaut, 0, spécifie la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour utiliser une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), passer `msgMapID`.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez créer une nouvelle fenêtre via [créer](#create), vous devez passer le nom d’une classe de fenêtre existante pour la `lpszClassName` paramètre. Pour obtenir un exemple, consultez la [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vue d’ensemble.  
  
 Il existe trois constructeurs :  
  
-   Le constructeur avec trois arguments est généralement appelée.  
  
-   Le constructeur avec deux arguments utilise le nom de classe à partir de **TBase::GetWndClassName**.  
  
-   Le constructeur sans argument est utilisé si vous souhaitez fournir les arguments ultérieurement. Vous devez fournir le nom de classe de fenêtre, objet de mappage de message et ID de mappage de message lorsque vous appelez ultérieurement **créer**.  
  
 Si vous sous-classer une fenêtre existante via [SubclassWindow](#subclasswindow), le `lpszClassName` valeur ne sera pas utilisée ; par conséquent, vous pouvez passer **NULL** pour ce paramètre.  
  
##  <a name="create"></a>  CContainedWindowT::Create  
 Appels [RegisterWndSuperclass](#registerwndsuperclass) pour inscrire une classe de fenêtre qui est basée sur une classe existante mais utilise [CContainedWindowT::WindowProc](#windowproc).  
  
```
HWND Create(  
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszClassName`  
 [in] Le nom d’une classe de fenêtre existante sur laquelle repose la fenêtre contenue.  
  
 `pObject`  
 [in] Pointeur vers l’objet conteneur qui déclare la table des messages. Cette classe de l’objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] Identifie la table des messages qui traitera les messages de la fenêtre de la relation contenant-contenu. La valeur par défaut, 0, spécifie la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour utiliser une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), passer `msgMapID`.  
  
 `hWndParent`  
 [in] Le handle de fenêtre parente ou propriétaire.  
  
 `rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure spécifiant la position de la fenêtre. Le `RECT` peuvent être passés par le pointeur ou par référence.  
  
 `szWindowName`  
 [in] Spécifie le nom de la fenêtre. La valeur par défaut est **NULL**.  
  
 `dwStyle`  
 [in] Le style de la fenêtre. La valeur par défaut est **WS_CHILD &#124; WS_VISIBLE**. Pour obtenir la liste des valeurs possibles, consultez [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) dans le Kit de développement logiciel Windows.  
  
 `dwExStyle`  
 [in] Le style de fenêtre étendus. La valeur par défaut est 0, ce qui signifie aucun style étendu. Pour obtenir la liste des valeurs possibles, consultez [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) dans le Kit de développement logiciel Windows.  
  
 `MenuOrID`  
 [in] Pour une fenêtre enfant, l’identificateur de la fenêtre. Pour une fenêtre de niveau supérieur, un descripteur de menu de la fenêtre. La valeur par défaut est **0 u**.  
  
 `lpCreateParam`  
 [in] Pointeur vers les données de création de la fenêtre. Pour obtenir une description complète, consultez la description pour le paramètre final [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, le handle de fenêtre qui vient d’être créé ; dans le cas contraire, **NULL**.  
  
### <a name="remarks"></a>Notes  
 Le nom de classe de fenêtre existante est enregistré dans [m_lpszClassName](#m_lpszclassname). **Créer** crée ensuite une fenêtre basée sur cette nouvelle classe. La fenêtre qui vient d’être créée est automatiquement joint à la `CContainedWindowT` objet.  
  
> [!NOTE]
>  N’appelez pas **créer** si vous avez déjà appelé [SubclassWindow](#subclasswindow).  
  
> [!NOTE]
>  Si 0 est utilisé comme valeur pour le `MenuOrID` paramètre, il doit être spécifié en tant que 0 u (valeur par défaut) pour éviter une erreur du compilateur.  
  
##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc  
 Appelé par [WindowProc](#windowproc) pour traiter les messages non gérées par la table des messages.  
  
```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Paramètres  
 `uMsg`  
 [in] Le message est envoyé à la fenêtre.  
  
 `wParam`  
 [in] Plus d’informations spécifique au message.  
  
 `lParam`  
 [in] Plus d’informations spécifique au message.  
  
### <a name="return-value"></a>Valeur de retour  
 Le résultat du traitement du message.  
  
### <a name="remarks"></a>Notes  
 Par défaut, `DefWindowProc` appelle la [CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) fonction Win32 pour envoyer les informations de message à la procédure de fenêtre spécifiée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage  
 Retourne le message actuel ( **m_pCurrentMsg**).  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le message en cours, empaqueté dans la `MSG` structure.  
  
##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID  
 Contient l’identificateur de la table des messages en cours d’utilisation de la fenêtre de relation contenant-contenue.  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>Notes  
 Cette table des messages doit être déclarée dans l’objet conteneur.  
  
 La table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est toujours identifié par zéro. Une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifié par `msgMapID`.  
  
 `m_dwMsgMapID` est d’abord initialisée par le constructeur et peut être modifiée en appelant [SwitchMessageMap](#switchmessagemap). Pour obtenir un exemple, consultez la [vue d’ensemble de CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).  
  
##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName  
 Spécifie le nom d’une classe de fenêtre existante.  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>Notes  
 Lorsque vous créez une fenêtre, [créer](#create) enregistre une nouvelle classe de fenêtre qui est basée sur cette classe existante mais utilise [CContainedWindowT::WindowProc](#windowproc).  
  
 `m_lpszClassName` est initialisé par le constructeur. Pour obtenir un exemple, consultez la [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) vue d’ensemble.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc  
 Si la fenêtre contenue est sous-classée, `m_pfnSuperWindowProc` pointe vers la procédure de fenêtre d’origine de la classe de fenêtre.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Notes  
 Si la fenêtre de relation contenant-contenue est la superclasse, ce qui signifie qu’il est basé sur une classe de fenêtre qui modifie une classe existante, `m_pfnSuperWindowProc` pointe vers la procédure de fenêtre de la classe de fenêtre existante.  
  
 Le [DefWindowProc](#defwindowproc) méthode envoie des informations de message à la procédure de fenêtre enregistrée dans `m_pfnSuperWindowProc`.  
  
##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject  
 Pointe vers l’objet contenant le `CContainedWindowT` objet.  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>Notes  
 Ce conteneur, dont la classe doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md), déclare le mappage de message utilisé par la fenêtre de relation contenant-contenue.  
  
 `m_pObject` est initialisé par le constructeur. Pour obtenir un exemple, consultez la [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) vue d’ensemble.  
  
##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass  
 Appelé par [créer](#create) pour inscrire la classe de fenêtre de la fenêtre contenue.  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, un atom qui identifie de façon unique la classe de fenêtre en cours d’inscription ; Sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette classe de fenêtre est basée sur une classe existante mais utilise [CContainedWindowT::WindowProc](#windowproc). Procédure de fenêtre et de nom de la classe de fenêtre existante sont enregistrés dans [m_lpszClassName](#m_lpszclassname) et [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), respectivement.  
  
##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow  
 Les sous-classes de la fenêtre est identifiée par `hWnd` et l’attache à le `CContainedWindowT` objet.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWnd`  
 [in] Le handle de fenêtre sous-classée.  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la fenêtre est correctement sous-classé ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 La fenêtre sous-classée utilise désormais [CContainedWindowT::WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  N’appelez pas `SubclassWindow` si vous avez déjà appelé [créer](#create).  
  
##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap  
 Modifie le mappage de message est utilisé pour traiter les messages de la fenêtre de la relation contenant-contenu.  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwMsgMapID`  
 [in] Identificateur de la carte de message. Pour utiliser le mappage de message par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), transférez la valeur zéro. Pour utiliser une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), passer `msgMapID`.  
  
### <a name="remarks"></a>Notes  
 La table des messages doit être définie dans l’objet conteneur.  
  
 Initialement, vous spécifiez l’identificateur de carte dans le constructeur.  
  
##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow  
 Détache la fenêtre sous-classé à partir de la `CContainedWindowT` de l’objet et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bForce`  
 [in] La valeur **TRUE** pour forcer la procédure de fenêtre d’origine pour être restaurée même si la procédure de fenêtre pour ce `CContainedWindowT` objet n’est pas actuellement actif. Si `bForce` a la valeur **FALSE** et la procédure de fenêtre pour ce `CContainedWindowT` objet n’est pas actif, la procédure de fenêtre d’origine n’est pas restaurée.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de fenêtre précédemment sous-classée. Si `bForce` a la valeur **FALSE** et la procédure de fenêtre pour ce `CContainedWindowT` objet n’est pas actuellement actif, retourne **NULL**.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode uniquement si vous souhaitez restaurer la procédure de fenêtre d’origine avant la destruction de la fenêtre. Dans le cas contraire, [WindowProc](#windowproc) fera automatiquement lorsque la fenêtre est détruite.  
  
##  <a name="windowproc"></a>  CContainedWindowT::WindowProc  
 Cette méthode statique implémente la procédure de fenêtre.  
  
```
static LRESULT CALLBACK WindowProc(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWnd`  
 [in] Le handle de fenêtre.  
  
 `uMsg`  
 [in] Le message est envoyé à la fenêtre.  
  
 `wParam`  
 [in] Plus d’informations spécifique au message.  
  
 `lParam`  
 [in] Plus d’informations spécifique au message.  
  
### <a name="return-value"></a>Valeur de retour  
 Le résultat du traitement du message.  
  
### <a name="remarks"></a>Notes  
 `WindowProc` Indique les messages à la table des messages identifié par [m_dwMsgMapID](#m_dwmsgmapid). Si nécessaire, `WindowProc` appelle [DefWindowProc](#defwindowproc) pour le traitement des messages supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [CWindow (classe)](../../atl/reference/cwindow-class.md)   
 [Classe de CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Classe de CMessageMap](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
