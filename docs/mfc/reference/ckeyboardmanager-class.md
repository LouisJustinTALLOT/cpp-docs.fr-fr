---
title: Ckeyboardmanager, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
dev_langs:
- C++
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 105a6310968844336ead5c787586d547f3952e57
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338984"
---
# <a name="ckeyboardmanager-class"></a>Ckeyboardmanager, classe
Gère les tables de touches de raccourci pour la fenêtre frame principale et les fenêtres frames enfants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CKeyboardManager : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Construit un objet `CKeyboardManager`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CKeyboardManager::CleanUp](#cleanup)|Efface les tables de touches de raccourci.|  
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Récupère la touche de raccourci par défaut pour la commande spécifiée et la fenêtre.|  
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Détermine si une clé est gérée par la table d’accélérateurs.|  
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Indique si un caractère imprimable.|  
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Indique si les menus affichent toutes les touches de raccourci pour une commande ou uniquement la touche de raccourci par défaut.|  
|[CKeyboardManager::LoadState](#loadstate)|Charge les tables de touches de raccourci à partir du Registre Windows.|  
|[CKeyboardManager::ResetAll](#resetall)|Recharge les tables de clés de raccourci à partir de la ressource d’application.|  
|[CKeyboardManager::SaveState](#savestate)|Enregistre le raccourci de tables de clés dans le Registre Windows.|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Spécifie si le framework affiche toutes les touches de raccourci pour toutes les commandes ou une touche de raccourci unique pour chaque commande. Cette méthode n’affecte pas les commandes qui n'ont qu’une seule touche de raccourci associé.|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Convertit un caractère en son Registre supérieure.|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Met à jour une table de clés de raccourci avec une nouvelle table de clé de raccourci.|  
  
## <a name="remarks"></a>Notes  
 Les membres de cette classe vous permettent d’enregistrer et charger des tables de clés de raccourci dans le Registre Windows, utilisez un modèle pour mettre à jour les tables de clés contextuels et trouver la touche de raccourci par défaut pour une commande dans une fenêtre frame. En outre, le `CKeyboardManager` objet vous permet de contrôler comment les touches de raccourci sont affichées à l’utilisateur.  
  
 Vous ne devez pas créer un `CKeyboardManager` objet manuellement. Il sera créé automatiquement par l’infrastructure de votre application. Toutefois, vous devez appeler [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) pendant le processus d’initialisation de votre application. Pour obtenir un pointeur vers le Gestionnaire de clavier pour votre application, appelez [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment récupérer un pointeur vers un `CKeyboardManager` de l’objet à partir d’un `CWinAppEx` classe et comment afficher toutes les touches de raccourci associées aux commandes de menu. Cet extrait de code fait partie de la [exemple des Pages personnalisées](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxkeyboardmanager.h  
  
##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager  
 Construit un objet `CKeyboardManager`.  
  
```  
CKeyboardManager();
```  
  
### <a name="remarks"></a>Notes  
 Dans la plupart des cas, vous n’avez pas à créer un `CKeyboardManager` directement. Par défaut, l’infrastructure crée un pour vous. Pour obtenir un pointeur vers le `CKeyboardManager`, appelez [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Si vous créez une manuellement, vous devez l’initialiser avec la méthode [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).  
  
##  <a name="cleanup"></a>  CKeyboardManager::CleanUp  
 Libère le `CKeyboardManager` ressources et efface tous les mappages de touches de raccourci.  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les touches de raccourci, consultez [personnalisation du clavier et souris](../../mfc/keyboard-and-mouse-customization.md).  
  
 Il est inutile d’appeler cette fonction lorsque vous quittez l’application, car le framework appelle automatiquement au cours de fermeture de l’application.  
  
##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator  
 Récupère la touche de raccourci par défaut pour la commande spécifiée et la fenêtre.  
  
```  
static BOOL FindDefaultAccelerator(
    UINT uiCmd,  
    CString& str,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmd*  
 ID de la commande.  
  
 [out] *str*  
 Référence à un objet `CString`.  
  
 [in] *pWndFrame*  
 Pointeur vers une fenêtre frame.  
  
 [in] *bIsDefaultFrame*  
 Spécifie si la fenêtre frame est la fenêtre de frame par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le raccourci est trouvé ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode recherche la commande spécifiée par *uiCmd* et récupère la touche de raccourci par défaut. Ensuite, la méthode accepte la chaîne associée à cette touche de raccourci et écrit la valeur pour le *str* paramètre.  
  
##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled  
 Détermine si la clé spécifiée est gérée par le [ckeyboardmanager, classe](../../mfc/reference/ckeyboardmanager-class.md).  
  
```  
static BOOL __stdcall IsKeyHandled(
    WORD nKey,  
    BYTE fVirt,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *nKey*|Clé à vérifier.|  
|[in] *fVirt*|Spécifie le comportement de la touche de raccourci. Pour obtenir la liste des valeurs possibles, consultez [accélération Structure](http://msdn.microsoft.com/library/windows/desktop/ms646340).|  
|[in] *pWndFrame*|Une fenêtre frame. Cette méthode détermine si une touche de raccourci est gérée dans ce frame.|  
|[in] *bIsDefaultFrame*|Un paramètre booléen qui indique si *pWndFrame* est la fenêtre de frame par défaut.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la touche de raccourci est gérée. FALSE si la clé n’est pas gérée ou si *pWndFrame* a la valeur NULL.  
  
### <a name="remarks"></a>Notes  
 Les paramètres d’entrée doivent correspondre à l’entrée dans la table d’accélérateurs les deux pour *nKey* et *fVirt* pour déterminer si une touche de raccourci est gérée dans *pWndFrame*.  
  
##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable  
 Indique si un caractère imprimable.  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *nChar*|Le caractère qui vérifie cette méthode.|  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le caractère imprimable, zéro si elle n’est pas.  
  
### <a name="remarks"></a>Notes  
 Cette méthode échoue si un appel à [GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299) échoue.  
  
##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators  
 Indique si les menus affichent toutes les touches de raccourci associées aux commandes de menu ou uniquement les touches de raccourci par défaut.  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’application répertorie toutes les touches de raccourci pour les commandes de menu ; 0 si l’application affiche uniquement les touches de raccourci par défaut.  
  
### <a name="remarks"></a>Notes  
 L’application répertorie les touches de raccourci pour les commandes de menu dans la barre de menus. Utilisez la fonction [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) pour contrôler si l’application répertorie toutes les touches de raccourci ou simplement les touches de raccourci par défaut.  
  
##  <a name="loadstate"></a>  CKeyboardManager::LoadState  
 Charge les tables de touches de raccourci à partir du Registre Windows.  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszProfileName*  
 Le chemin d’accès du Registre où `CKeyboardManager` les données sont enregistrées.  
  
 [in] *pDefaultFrame*  
 Pointeur vers une fenêtre frame à utiliser comme la fenêtre par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’état a été chargé avec succès ou 0 dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Si le *lpszProfileName* paramètre est NULL, cette méthode vérifie l’emplacement de Registre par défaut `CKeyboardManager` données. L’emplacement de Registre par défaut est spécifié par le [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md). Les données doivent être écrites précédemment avec la méthode [CKeyboardManager::SaveState](#savestate).  
  
 Si vous ne spécifiez pas une fenêtre par défaut, la fenêtre frame principale de votre application sera utilisée.  
  
##  <a name="resetall"></a>  CKeyboardManager::ResetAll  
 Recharge les tables de clés de raccourci à partir de la ressource d’application.  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction efface les raccourcis stockées dans le `CKeyboardManager` instance. Il sera ensuite rechargez l’état du Gestionnaire de clavier à partir de la ressource d’application.  
  
##  <a name="savestate"></a>  CKeyboardManager::SaveState  
 Enregistre le raccourci de tables de clés dans le Registre Windows.  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszProfileName*  
 Le chemin d’accès de Registre pour enregistrer le `CKeyboardManager` état.  
  
 [in] *pDefaultFrame*  
 Pointeur vers une fenêtre frame qui devient la fenêtre par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’état de gestionnaire de clavier a été enregistré avec succès, ou 0 dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Si le *lpszProfileName* paramètre est NULL, cette méthode écrit le `CKeyboardManager` à l’état de l’emplacement par défaut spécifié par le [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md). Si vous spécifiez un emplacement, vous pouvez charger les données ultérieurement à l’aide de la méthode [CKeyboardManager::LoadState](#loadstate).  
  
 Si vous ne spécifiez pas une fenêtre par défaut, la fenêtre frame principale sera utilisée en tant que la fenêtre par défaut.  
  
##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators  
 Affiche toutes les touches de raccourci associées aux commandes de menu.  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bShowAll*  
 Si la valeur est TRUE, toutes les touches de raccourci seront affichera. Si la valeur est FALSE, la première touche de raccourci s’affichera.  
  
 [in] *lpszDelimiter*  
 Chaîne à insérer entre les touches de raccourci. Ce séparateur n’a aucun effet si seulement une touche de raccourci s’affiche.  
  
### <a name="remarks"></a>Notes  
 Par défaut, si une commande contient plus d’une touche de raccourci associée, uniquement la première touche de raccourci s’affichera. Cette fonction vous permet de répertorier toutes les touches de raccourci associés à toutes les commandes.  
  
 Les touches de raccourci apparaît en regard de la commande dans la barre de menus. Si les touches de raccourci sont affichées, la chaîne fournie par *lpszDelimiter* pour séparer les touches de raccourci individuels.  
  
##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper  
 Convertit un caractère en son Registre supérieure.  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nChar*  
 Caractère à convertir.  
  
### <a name="return-value"></a>Valeur de retour  
 Le caractère qui représente le Registre supérieur du paramètre d’entrée.  
  
##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable  
 Met à jour une table de clés de raccourci avec une nouvelle table de clé de raccourci.  
  
```  
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    LPACCEL lpAccel,  
    int nSize,  
    CFrameWnd* pDefaultFrame = NULL);

 
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    HACCEL hAccelNew,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pTemplate*  
 Pointeur vers un modèle de document.  
  
 [in] *lpAccel*  
 Pointeur vers la nouvelle touche de raccourci.  
  
 [in] *nSize*  
 La taille de la nouvelle table de raccourci.  
  
 [in] *pDefaultFrame*  
 Pointeur vers la fenêtre de frame par défaut.  
  
 [in] *hAccelNew*  
 Handle vers la nouvelle table de raccourci.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode réussit ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet de remplacer la table de raccourci existant avec nouvelles touches de raccourci pour plusieurs objets de fenêtre frame. La fonction reçoit un modèle de document en tant que paramètre pour obtenir l’accès à tous les objets de fenêtre frame connecté au modèle de document donné.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md)



