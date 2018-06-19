---
title: Classe de CWindowImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4884bbacd03675d00cb1a49b937265ab5faa2835
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366154"
---
# <a name="cwindowimpl-class"></a>Classe de CWindowImpl
Fournit des méthodes pour créer ou sous-classer une fenêtre.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre nouvelle classe, dérivée de `CWindowImpl`.  
  
 *TBase*  
 Classe de base de votre classe. Par défaut, la classe de base est [CWindow](../../atl/reference/cwindow-class.md).  
  
 `TWinTraits`  
 A [classe de traits](../../atl/understanding-window-traits.md) qui définit les styles de votre fenêtre. La valeur par défaut est `CControlWinTraits`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWindowImpl::Create](#create)|Crée une fenêtre.|  
  
### <a name="cwindowimplbaset-methods"></a>Méthodes CWindowImplBaseT  
  
|||  
|-|-|  
|[DefWindowProc](#defwindowproc)|Fournit le traitement du message par défaut.|  
|[GetCurrentMessage](#getcurrentmessage)|Retourne le message actuel.|  
|[GetWindowProc](#getwindowproc)|Retourne la procédure de fenêtre active.|  
|[OnFinalMessage](#onfinalmessage)|Appelée après réception du dernier message (généralement `WM_NCDESTROY`).|  
|[SubclassWindow](#subclasswindow)|Sous-classe une fenêtre.|  
|[UnsubclassWindow](#unsubclasswindow)|Restaure une fenêtre précédemment sous-classée.|  
  
### <a name="static-methods"></a>Méthodes statiques  
  
|||  
|-|-|  
|[GetWndClassInfo](#getwndclassinfo)|Retourne une instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), qui gère les informations de classe de fenêtre.|  
|[WindowProc](#windowproc)|Traite les messages envoyés à la fenêtre.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Pointe vers la procédure de fenêtre d'origine de la classe de fenêtre.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser `CWindowImpl` pour créer une fenêtre ou une sous-classe une fenêtre existante. le `CWindowImpl` procédure de fenêtre utilise une table des messages pour diriger les messages vers les gestionnaires appropriés.  
  
 `CWindowImpl::Create` Crée une fenêtre basée sur les informations de classe de fenêtre qui sont gérées par [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` contient le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (macro), ce qui signifie que `CWndClassInfo` enregistre une nouvelle classe de fenêtre. Si vous souhaitez surclasser une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et inclure le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) (macro). Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre basée sur une classe existante mais utilise `CWindowImpl::WindowProc`. Par exemple :  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Étant donné que `CWndClassInfo` gère les informations d'une seule classe de fenêtre, chaque fenêtre créée via une instance de `CWindowImpl` est basée sur la même classe de fenêtre.  
  
 `CWindowImpl` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CWindowImpl` et remplace la procédure de fenêtre par `CWindowImpl::WindowProc`. Chaque instance de `CWindowImpl` peut sous-classer une fenêtre différente.  
  
> [!NOTE]
>  Pour toute donnée `CWindowImpl` de l’objet, appelez **créer** ou `SubclassWindow`. N'appelez pas les deux méthodes sur le même objet.  
  
 En plus de `CWindowImpl`, ATL fournit [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) pour créer une fenêtre qui est contenue dans un autre objet.  
  
 Le destructeur de classe de base (~ **CWindowImplRoot**) garantit que la fenêtre disparaît avant la destruction de l’objet.  
  
 `CWindowImpl` dérive de **CWindowImplBaseT**, qui dérive à son **CWindowImplRoot**, lequel dérive **TBase** et [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
|Pour plus d'informations sur|Voir|  
|--------------------------------|---------|  
|Création de contrôles|[Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Utilisation de fenêtres dans ATL|[ATL, classes de fenêtre](../../atl/atl-window-classes.md)|  
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlwin.h  
  
##  <a name="create"></a>  CWindowImpl::Create  
 Crée une fenêtre basée sur une nouvelle classe de fenêtre.  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 [in] Le handle de fenêtre parente ou propriétaire.  
  
 `rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure spécifiant la position de la fenêtre. Le `RECT` peuvent être passés par le pointeur ou par référence.  
  
 `szWindowName`  
 [in] Spécifie le nom de la fenêtre. La valeur par défaut est **NULL**.  
  
 `dwStyle`  
 [in] Le style de la fenêtre. Cette valeur est combinée avec le style fourni par la classe de caractéristiques de la fenêtre. La valeur par défaut donne les caractéristiques de classe un contrôle total sur le style. Pour obtenir la liste des valeurs possibles, consultez [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) dans le Kit de développement logiciel Windows.  
  
 `dwExStyle`  
 [in] Le style de fenêtre étendus. Cette valeur est combinée avec le style fourni par la classe de caractéristiques de la fenêtre. La valeur par défaut donne les caractéristiques de classe un contrôle total sur le style. Pour obtenir la liste des valeurs possibles, consultez [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) dans le Kit de développement logiciel Windows.  
  
 `MenuOrID`  
 [in] Pour une fenêtre enfant, l’identificateur de la fenêtre. Pour une fenêtre de niveau supérieur, un descripteur de menu de la fenêtre. La valeur par défaut est **0 u**.  
  
 `lpCreateParam`  
 [in] Pointeur vers les données de création de la fenêtre. Pour obtenir une description complète, consultez la description pour le paramètre final [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, le handle de fenêtre qui vient d’être créé. Dans le cas contraire, **NULL**.  
  
### <a name="remarks"></a>Notes  
 **Créer** enregistre tout d’abord la classe de fenêtre si elle n’a pas encore été enregistré. La fenêtre qui vient d’être créée est automatiquement joint à la `CWindowImpl` objet.  
  
> [!NOTE]
>  N’appelez pas **créer** si vous avez déjà appelé [SubclassWindow](#subclasswindow).  
  
 Pour utiliser une classe de fenêtre qui est basée sur une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et inclure le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) (macro). Procédure de fenêtre de la classe de fenêtre existante est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Pour plus d’informations, consultez la [CWindowImpl](../../atl/reference/cwindowimpl-class.md) vue d’ensemble.  
  
> [!NOTE]
>  Si 0 est utilisé comme valeur pour le `MenuOrID` paramètre, il doit être spécifié en tant que 0 u (valeur par défaut) pour éviter une erreur du compilateur.  
  
##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc  
 Appelé par [WindowProc](#windowproc) pour traiter les messages non gérées par la table des messages.  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
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
  
 La fonction sans paramètres récupère automatiquement les paramètres nécessaires à partir du message en cours.  
  
##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage  
 Retourne le message actuel, empaqueté dans la `MSG` structure.  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le message en cours.  
  
##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc  
 Retourne `WindowProc`, la procédure de fenêtre en cours.  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La procédure de fenêtre en cours.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour remplacer la procédure de fenêtre par les vôtres.  
  
##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo  
 Appelé par [créer](#create) pour accéder aux informations de classe de fenêtre.  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).  
  
### <a name="remarks"></a>Notes  
 Par défaut, `CWindowImpl` obtient cette méthode via la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro, qui spécifie une nouvelle classe de fenêtre.  
  
 Pour surclasser une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et inclure le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro pour remplacer `GetWndClassInfo`. Pour plus d’informations, consultez la [CWindowImpl](../../atl/reference/cwindowimpl-class.md) vue d’ensemble.  
  
 Outre l’utilisation de la `DECLARE_WND_CLASS` et `DECLARE_WND_SUPERCLASS` macros, vous pouvez remplacer `GetWndClassInfo` par votre propre implémentation.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc  
 En fonction de la fenêtre, pointe vers une des procédures de fenêtre suivant.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Notes  
  
|Type de fenêtre|Procédure de fenêtre|  
|--------------------|----------------------|  
|Une fenêtre basée sur une nouvelle classe de fenêtre spécifiée par le biais du [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (macro).|Le [DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) fonction Win32.|  
|Une fenêtre basée sur une classe de fenêtre qui modifie une classe existante, spécifiée par le biais du [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) (macro).|Procédure de fenêtre de la classe de fenêtre existante.|  
|Une fenêtre sous-classée.|Procédure de fenêtre d’origine de la fenêtre sous-classée.|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc) envoie plus d’informations à enregistrer dans la procédure de fenêtre de message `m_pfnSuperWindowProc`.  
  
##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage  
 Appelé après réception du dernier message (généralement `WM_NCDESTROY`).  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWnd`  
 [in] Un handle de fenêtre en cours de destruction.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de `OnFinalMessage` ne fait rien, mais vous pouvez remplacer cette fonction pour gérer de nettoyage avant la destruction d’une fenêtre. Si vous souhaitez supprimer automatiquement votre objet lors de la destruction de la fenêtre, vous pouvez appeler `delete this;` dans cette fonction.  
  
##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow  
 Les sous-classes de la fenêtre est identifiée par `hWnd` et l’attache à le `CWindowImpl` objet.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWnd`  
 [in] Le handle de fenêtre sous-classée.  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la fenêtre est correctement sous-classé ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 La fenêtre sous-classée utilise désormais [CWindowImpl::WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  N’appelez pas `SubclassWindow` si vous avez déjà appelé [créer](#create).  
  
##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow  
 Détache la fenêtre sous-classé à partir de la `CWindowImpl` de l’objet et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de fenêtre précédemment sous-classée.  
  
##  <a name="windowproc"></a>  CWindowImpl::WindowProc  
 Cette fonction statique implémente la procédure de fenêtre.  
  
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
 `WindowProc` utilise la table des messages par défaut (déclaré avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) pour diriger les messages vers les gestionnaires appropriés. Si nécessaire, `WindowProc` appelle [DefWindowProc](#defwindowproc) pour le traitement des messages supplémentaires. Si le message final n’est pas géré, `WindowProc` effectue les opérations suivantes :  
  
-   Effectue unsubclassing si la fenêtre a été unsubclassed.  
  
-   Efface `m_hWnd`.  
  
-   Appels [OnFinalMessage](#onfinalmessage) avant la destruction de la fenêtre.  
  
 Vous pouvez substituer `WindowProc` pour fournir un autre mécanisme de gestion des messages.  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Classe de CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
