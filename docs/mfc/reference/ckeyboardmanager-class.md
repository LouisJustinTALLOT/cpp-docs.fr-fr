---
title: CKeyboardManager, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: e67bbb18b6a87edfaa4bc4c410ec28eb613ed51d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841491"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager, classe

Gère les tables de touches de raccourci pour la fenêtre frame principale et les fenêtres frames enfants.

## <a name="syntax"></a>Syntaxe

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|[CKeyboardManager :: CKeyboardManager](#ckeyboardmanager)|Construit un objet `CKeyboardManager`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CKeyboardManager :: CleanUp](#cleanup)|Efface les tables de touches de raccourci.|
|[CKeyboardManager :: FindDefaultAccelerator](#finddefaultaccelerator)|Récupère la touche de raccourci par défaut pour la commande et la fenêtre spécifiées.|
|[CKeyboardManager :: IsKeyHandled](#iskeyhandled)|Détermine si une clé est gérée par la table d’accélérateurs.|
|[CKeyboardManager :: IsKeyPrintable](#iskeyprintable)|Indique si un caractère peut être imprimé.|
|[CKeyboardManager :: IsShowAllAccelerators](#isshowallaccelerators)|Indique si les menus affichent toutes les touches de raccourci d’une commande ou uniquement la touche de raccourci par défaut.|
|[CKeyboardManager :: LoadState](#loadstate)|Charge les tables de touches de raccourci à partir du Registre Windows.|
|[CKeyboardManager :: ResetAll](#resetall)|Recharge les tables de touches de raccourci à partir de la ressource d’application.|
|[CKeyboardManager :: saveste](#savestate)|Enregistre les tables de touches de raccourci dans le Registre Windows.|
|[CKeyboardManager :: ShowAllAccelerators](#showallaccelerators)|Spécifie si l’infrastructure affiche toutes les touches de raccourci pour toutes les commandes, ou une touche de raccourci unique pour chaque commande. Cette méthode n’affecte pas les commandes qui n’ont qu’une seule touche de raccourci associée.|
|[CKeyboardManager :: TranslateCharToUpper](#translatechartoupper)|Convertit un caractère en son registre supérieur.|
|[CKeyboardManager :: UpdateAccelTable](#updateacceltable)|Met à jour une table de raccourcis clavier avec une nouvelle table de touches de raccourci.|

## <a name="remarks"></a>Notes

Les membres de cette classe vous permettent d’enregistrer et de charger des tables de touches de raccourci dans le Registre Windows, d’utiliser un modèle pour mettre à jour les tables de clés courtes et de rechercher la touche de raccourci par défaut pour une commande dans une fenêtre frame. En outre, l' `CKeyboardManager` objet vous permet de contrôler la façon dont les touches de raccourci sont affichées à l’utilisateur.

Vous ne devez pas créer un `CKeyboardManager` objet manuellement. Il sera créé automatiquement par l’infrastructure de votre application. Toutefois, vous devez appeler [CWinAppEx :: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) pendant le processus d’initialisation de votre application. Pour obtenir un pointeur vers le gestionnaire de clavier de votre application, appelez [CWinAppEx :: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer un pointeur vers un `CKeyboardManager` objet à partir d’une `CWinAppEx` classe, et comment afficher toutes les touches de raccourci associées aux commandes de menu. Cet extrait de code fait partie de l' [exemple de pages personnalisées](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxkeyboardmanager. h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a> CKeyboardManager :: CKeyboardManager

Construit un objet `CKeyboardManager`.

```
CKeyboardManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’avez pas besoin de créer un `CKeyboardManager` directement. Par défaut, le Framework en crée un pour vous. Pour obtenir un pointeur vers le `CKeyboardManager` , appelez [CWinAppEx :: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Si vous en créez une manuellement, vous devez l’initialiser à l’aide de la méthode [CWinAppEx :: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a> CKeyboardManager :: CleanUp

Libère les `CKeyboardManager` ressources et efface tous les mappages de touches de raccourci.

```
static void CleanUp();
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les touches de raccourci, consultez [Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md).

Vous n’avez pas à appeler cette fonction lorsque votre application se ferme, car le Framework l’appelle automatiquement pendant la fermeture de l’application.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a> CKeyboardManager :: FindDefaultAccelerator

Récupère la touche de raccourci par défaut pour la commande et la fenêtre spécifiées.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de la commande.

*Str*<br/>
à Référence à un `CString` objet.

*pWndFrame*<br/>
dans Pointeur vers une fenêtre frame.

*bIsDefaultFrame*<br/>
dans Spécifie si la fenêtre frame est la fenêtre frame par défaut.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le raccourci est trouvé ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode recherche la commande spécifiée par *uiCmd* et récupère la touche de raccourci par défaut. La méthode prend ensuite la chaîne associée à cette touche de raccourci et écrit la valeur dans le paramètre *Str* .

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a> CKeyboardManager :: IsKeyHandled

Détermine si la clé spécifiée est gérée par la [classe CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Paramètres

*nKey*\
dans Clé à vérifier.

*fVirt*\
dans Spécifie le comportement de la touche de raccourci. Pour obtenir la liste des valeurs possibles, consultez la rubrique [structure d’accélération](/windows/win32/api/winuser/ns-winuser-accel).

*pWndFrame*\
dans Fenêtre frame. Cette méthode détermine si une touche de raccourci est gérée dans ce frame.

*bIsDefaultFrame*\
dans Paramètre booléen qui indique si *pWndFrame* est la fenêtre frame par défaut.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la touche de raccourci est gérée. FALSe si la clé n’est pas gérée ou si *pWndFrame* a la valeur null.

### <a name="remarks"></a>Notes

Les paramètres d’entrée doivent correspondre à l’entrée de la table d’accélérateurs pour *nKey* et *fVirt* pour déterminer si une touche de raccourci est gérée dans *pWndFrame*.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a> CKeyboardManager :: IsKeyPrintable

Indique si un caractère peut être imprimé.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Paramètres

*nChar*\
dans Caractère vérifié par cette méthode.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le caractère est imprimable, zéro si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Cette méthode échoue si un appel à [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) échoue.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a> CKeyboardManager :: IsShowAllAccelerators

Indique si les menus affichent toutes les touches de raccourci associées aux commandes de menu ou uniquement les touches de raccourci par défaut.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’application répertorie toutes les touches de raccourci pour les commandes de menu ; 0 si l’application affiche uniquement les touches de raccourci par défaut.

### <a name="remarks"></a>Notes

L’application répertorie les touches de raccourci pour les commandes de menu dans la barre de menus. Utilisez la fonction [CKeyboardManager :: ShowAllAccelerators](#showallaccelerators) pour contrôler si l’application répertorie toutes les touches de raccourci ou uniquement les touches de raccourci par défaut.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a> CKeyboardManager :: LoadState

Charge les tables de touches de raccourci à partir du Registre Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chemin d’accès au registre où les `CKeyboardManager` données sont enregistrées.

*pDefaultFrame*<br/>
dans Pointeur vers une fenêtre frame à utiliser comme fenêtre par défaut.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’État a été chargé avec succès ou 0 dans le cas contraire.

### <a name="remarks"></a>Notes

Si le paramètre *lpszProfileName* est null, cette méthode vérifie l’emplacement du Registre par défaut pour les `CKeyboardManager` données. L’emplacement du Registre par défaut est spécifié par la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md). Les données doivent être écrites précédemment à l’aide de la méthode [CKeyboardManager :: saveste](#savestate).

Si vous ne spécifiez pas de fenêtre par défaut, la fenêtre frame principale de votre application est utilisée.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a> CKeyboardManager :: ResetAll

Recharge les tables de touches de raccourci à partir de la ressource d’application.

```cpp
void ResetAll();
```

### <a name="remarks"></a>Notes

Cette fonction efface les raccourcis stockés dans l' `CKeyboardManager` instance. Il recharge ensuite l’état du gestionnaire de clavier à partir de la ressource d’application.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a> CKeyboardManager :: saveste

Enregistre les tables de touches de raccourci dans le Registre Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
dans Chemin d’accès du Registre pour l’enregistrement de l' `CKeyboardManager` État.

*pDefaultFrame*<br/>
dans Pointeur vers une fenêtre frame qui devient la fenêtre par défaut.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’état du gestionnaire de clavier a été enregistré avec succès, ou 0 dans le cas contraire.

### <a name="remarks"></a>Notes

Si le paramètre *lpszProfileName* est null, cette méthode écrit l' `CKeyboardManager` État à l’emplacement par défaut spécifié par la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md). Si vous spécifiez un emplacement, vous pouvez charger les données ultérieurement à l’aide de la méthode [CKeyboardManager :: LoadState](#loadstate).

Si vous ne spécifiez pas de fenêtre par défaut, la fenêtre frame principale sera utilisée comme fenêtre par défaut.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a> CKeyboardManager :: ShowAllAccelerators

Affiche toutes les touches de raccourci associées aux commandes de menu.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Paramètres

*bShowAll*<br/>
dans Si la valeur est TRUE, toutes les touches de raccourci sont affichées. Si la valeur est FALSe, seule la première touche de raccourci sera affichée.

*lpszDelimiter*<br/>
dans Chaîne à insérer entre les touches de raccourci. Ce délimiteur n’a aucun effet si une seule touche de raccourci est affichée.

### <a name="remarks"></a>Notes

Par défaut, si plusieurs touches de raccourci sont associées à une commande, seule la première touche de raccourci sera affichée. Cette fonction vous permet de répertorier toutes les touches de raccourci associées à toutes les commandes.

Les touches de raccourci seront listées en regard de la commande dans la barre de menus. Si toutes les touches de raccourci sont affichées, la chaîne fournie par *lpszDelimiter* sépare les touches de raccourci individuelles.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a> CKeyboardManager :: TranslateCharToUpper

Convertit un caractère en son registre supérieur.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Paramètres

*nChar*<br/>
dans Caractère à convertir.

### <a name="return-value"></a>Valeur renvoyée

Caractère qui est le registre supérieur du paramètre d’entrée.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a> CKeyboardManager :: UpdateAccelTable

Met à jour une table de raccourcis clavier avec une nouvelle table de touches de raccourci.

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

*pTemplate*<br/>
dans Pointeur vers un modèle de document.

*lpAccel*<br/>
dans Pointeur vers la nouvelle touche de raccourci.

*nSize*<br/>
dans Taille du nouveau tableau de raccourcis.

*pDefaultFrame*<br/>
dans Pointeur vers la fenêtre frame par défaut.

*hAccelNew*<br/>
dans Handle vers le nouveau tableau de raccourcis.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour remplacer la table de raccourcis existante par de nouvelles touches de raccourci pour plusieurs objets de fenêtre frame. La fonction reçoit un modèle de document en tant que paramètre pour obtenir l’accès à tous les objets de fenêtre frame connectés au modèle de document donné.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx :: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Personnalisation du clavier et de la souris](../../mfc/keyboard-and-mouse-customization.md)
