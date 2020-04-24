---
title: Classe CMFCEditBrowseCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: d542af4a87b6f0a33c0344d1d3da76980f8c1a91
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752379"
---
# <a name="cmfceditbrowsectrl-class"></a>Classe CMFCEditBrowseCtrl

La `CMFCEditBrowseCtrl` classe prend en charge le contrôle de navigation de modification, qui est une boîte de texte modifiable qui contient en option un bouton de navigation. Lorsque l’utilisateur clique sur le bouton Parcourir, le contrôle effectue une action personnalisée ou affiche une boîte de dialogue standard qui contient un explorateur de fichiers ou de dossiers.

## <a name="syntax"></a>Syntaxe

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Constructeur par défaut.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Permet ou désactive (cache) le bouton de navigation.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Permet le bouton de navigation et met le contrôle de navigation de l’édition en mode *de navigation de fichier.*|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Permet le bouton de navigation et met le contrôle de navigation d’édition en mode de navigation de *dossier.*|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Retourne le mode de navigation actuel.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Appelé par le cadre après le contrôle de navigation de modification est mis à jour avec le résultat d’une action de navigation.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Appelé par le cadre après que l’utilisateur clique sur le bouton de navigation.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Redessiner le contrôle de navigation de navigation de modification en cours.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Appelé par le cadre pour dessiner le bouton de navigation.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Appelé par le cadre quand un nom de fichier illégal a été entré dans le contrôle de modification.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Pour la syntaxe et plus d’informations, voir [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Définit une image personnalisée pour le bouton de navigation.|

## <a name="remarks"></a>Notes

Utilisez un contrôle de navigation de modification pour sélectionner un nom de fichier ou de dossier. Optionnellement, utilisez le contrôle pour effectuer une action personnalisée comme pour afficher une boîte de dialogue. Vous pouvez afficher ou non le bouton de navigation, et vous pouvez appliquer une étiquette ou une image personnalisée sur le bouton.

Le *mode de navigation* du contrôle de navigation de modification détermine s’il affiche un bouton de navigation et quelle action se produit lorsque le bouton est cliqué. Pour plus d’informations, consultez la méthode [GetMode.](#getmode)

La `CMFCEditBrowseCtrl` classe prend en charge les modes suivants.

- **mode personnalisé**

   Une action personnalisée est effectuée lorsque l’utilisateur clique sur le bouton de navigation. Par exemple, vous pouvez afficher une boîte de dialogue spécifique à l’application.

- **mode fichier**

   Une boîte de dialogue standard de sélection de fichiers s’affiche lorsque l’utilisateur clique sur le bouton de navigation.

- **mode dossier**

   Une boîte de dialogue de sélection de dossiers standard s’affiche lorsque l’utilisateur clique sur le bouton de navigation.

## <a name="how-to-specify-an-edit-browse-control"></a>Comment-à: Spécifier un contrôle de navigation d’édition

Effectuez les étapes suivantes pour intégrer un contrôle de navigation de modification dans votre application :

1. Si vous souhaitez implémenter un mode de `CMFCEditBrowseCtrl` navigation personnalisé, dérivez votre propre classe de la classe, puis remplacez le [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) méthode. Dans la méthode de dépassement, exécutez une action de navigation personnalisée et mettez à jour le contrôle de navigation d’édition avec le résultat.

1. Intégrer soit `CMFCEditBrowseCtrl` l’objet, soit l’objet de contrôle de navigation de navigation dérivé dans l’objet de la fenêtre parente.

1. Si vous utilisez le **Class Wizard** pour créer une `CEdit`boîte de dialogue, ajoutez un contrôle de modification ( ) au formulaire de boîte de dialogue. Ajoutez également une variable pour accéder au contrôle de votre fichier d’en-tête. Dans votre fichier d’en-tête, `CEdit` `CMFCEditBrowseCtrl`modifiez le type de la variable de . Le contrôle de navigation de modification sera créé automatiquement. Si vous n’utilisez pas le **Class Wizard**, ajoutez une `CMFCEditBrowseCtrl` variable à votre fichier d’en-tête, puis appelez sa `Create` méthode.

1. Si vous ajoutez un contrôle de navigation de modification à une boîte de dialogue, utilisez l’outil **ClassWizard** pour configurer l’échange de données.

1. Appelez la méthode [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)ou [EnableBrowseButton](#enablebrowsebutton) pour définir le mode de navigation et afficher le bouton de navigation. Appelez la méthode [GetMode](#getmode) pour obtenir le mode de navigation actuel.

1. Pour fournir une image personnalisée pour le bouton de navigation, appelez la méthode [SetBrowseButtonImage](#setbrowsebuttonimage) ou remplacez la méthode [OnDrawBrowseButton.](#ondrawbrowsebutton)

1. Pour supprimer le bouton de navigation du contrôle de navigation de modification, appelez la méthode [EnableBrowseButton](#enablebrowsebutton) avec le paramètre *bEnable* défini à FALSE.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CMFCEditBrowseCtrl` deux `EnableFolderBrowseButton` méthodes `EnableFileBrowseButton`dans la classe: et . Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxeditbrowsectrl.h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton

Affiche ou n’affiche pas le bouton de navigation sur le contrôle de navigation de modification en cours.

```cpp
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
VRAI pour afficher le bouton de navigation; FALSE de ne pas afficher le bouton de navigation. La valeur par défaut est TRUE.

*szLabel (en)*<br/>
L’étiquette affichée sur le bouton de navigation. La valeur par défaut est " **...**".

### <a name="remarks"></a>Notes

Si le paramètre *bEnable* est VRAI, implémentez une action personnalisée pour effectuer lorsque le bouton de navigation est cliqué. Pour mettre en œuvre une `CMFCEditBrowseCtrl` action personnalisée, dérivez une classe de la classe, puis remplacez sa méthode [OnBrowse.](#onbrowse)

Si le *paramètre bEnable* est VRAI, le `BrowseMode_Default`mode de navigation du contrôle est ; sinon, le mode `BrowseMode_None`de navigation est . Pour plus d’informations sur les modes de navigation, consultez la méthode [GetMode.](#getmode)

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton

Affiche le bouton de navigation sur le contrôle de navigation de navigation de modification en cours et met le contrôle en mode *de navigation de fichier.*

```cpp
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Paramètres

*lpszDefExt*<br/>
Spécifie l’extension de nom de fichier par défaut utilisée dans la boîte de dialogue de sélection de fichier. La valeur par défaut est NULL.

*lpszFilter (lpszFilter)*<br/>
Spécifie la chaîne de filtrage par défaut utilisée dans la boîte de dialogue de sélection de fichier. La valeur par défaut est NULL.

*dwFlags*<br/>
Indicateurs de boîte de dialogue. La valeur par défaut est une combinaison (OR) au niveau du bit de OFN_HIDEREADONLY et OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Notes

Quand le contrôle de zone de modification est en mode de navigation de fichiers et que l'utilisateur clique sur le bouton parcourir, le contrôle affiche la boîte de dialogue de sélection de fichier standard.

Pour une liste complète des drapeaux disponibles, voir [la structure OPENFILENAME](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton

Affiche le bouton de navigation sur le contrôle de navigation de navigation de modification en cours et met le contrôle en mode *de navigation de dossier.*

```cpp
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Notes

Lorsque le contrôle de navigation de modification est en mode de navigation de dossier et que l’utilisateur clique sur le bouton de navigation, le contrôle affiche la boîte de dialogue de sélection de dossier standard.

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEditBrowseCtrl::GetMode

Récupère le mode de navigation du contrôle de navigation de l’édition actuelle.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Valeur de retour

L’une des valeurs de recensement qui spécifie le mode actuel de l’édition de navigation de contrôle. Le mode de navigation détermine si le cadre affiche le bouton de navigation et quelle action se produit lorsqu’un utilisateur clique sur ce bouton.

Le tableau ci-dessous répertorie les valeurs de retour possibles.

|Valeur|Description|
|-----------|-----------------|
|`BrowseMode_Default`|**mode personnalisé**. Une action définie par le programmeur est effectuée.|
|`BrowseMode_File`|**mode fichier**. La boîte de dialogue standard du navigateur de fichiers s’affiche.|
|`BrowseMode_Folder`|**mode dossier**. La boîte de dialogue standard du navigateur de dossier est affichée.|
|`BrowseMode_None`|Le bouton de navigation n’est pas affiché.|

### <a name="remarks"></a>Notes

Par défaut, `CMFCEditBrowseCtrl` un objet `BrowseMode_None` est parasé par mode. Modifier le mode de navigation avec le [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), et [CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton) méthodes.

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate

Appelé par le cadre après le contrôle de navigation de modification est mis à jour avec le résultat d’une action de navigation.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour mettre en œuvre une action personnalisée.

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse

Appelé par le cadre après que l’utilisateur clique sur le bouton de navigation du contrôle de navigation de l’édition.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Notes

Utilisez cette méthode pour exécuter le code personnalisé lorsque l’utilisateur clique sur le bouton de navigation du contrôle de navigation de modification. Dérivez votre propre `CMFCEditBrowseCtrl` classe de `OnBrowse` la classe et remplacez sa méthode. Dans cette méthode, implémentez une action personnalisée de navigation et mettez à jour optionnellement la boîte de texte du contrôle de navigation de modification. Dans votre application, utilisez la méthode [EnableBrowseButton](#enablebrowsebutton) pour mettre le contrôle de navigation d’édition en mode *de navigation personnalisé.*

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout

Redessiner le contrôle de navigation de navigation de modification en cours.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsque le mode de navigation de l’édition de navigation change. Pour plus d’informations, voir [CMFCEditBrowseCtrl::GetMode](#getmode).

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton

Appelé par le cadre pour dessiner le bouton de navigation sur le contrôle de navigation d’édition.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers un contexte de périphérique.

*Rect*<br/>
Le rectangle de délimitation du bouton de navigation.

*bIsButtonPressed*<br/>
VRAI si le bouton est appuyé; autrement, FALSE.

*bIsButtonHot (en)*<br/>
VRAI si le bouton est mis en surbrillance; autrement, FALSE.

### <a name="remarks"></a>Notes

Remplacer cette fonction dans une classe dérivée pour personnaliser l’apparence du bouton de navigation.

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage

Définit une image personnalisée sur le bouton de navigation du contrôle de navigation d’édition.

```cpp
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>Paramètres

*hIcon (en)*<br/>
Le manche d’une icône.

*hBitmap (en)*<br/>
Le manche d’un bitmap.

*uiBmpResId*<br/>
L’ID de ressource d’un bitmap.

*bAutoDestroy*<br/>
VRAI pour supprimer l’icône spécifiée ou bitmap lorsque cette méthode sort; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour appliquer une image personnalisée sur le bouton de navigation. Par défaut, le cadre obtient une image standard lorsque le contrôle de navigation de modification est en mode *de navigation de fichier* ou de connexion de *dossier.*

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName

Appelé par le cadre quand un nom de fichier illégal a été entré dans le contrôle de modification.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Paramètres

*strFileName (en)*<br/>
Spécifie le nom illégal du fichier.

### <a name="return-value"></a>Valeur de retour

Devrait retourner FALSE si ce nom de fichier ne peut pas être transmis plus loin au dialogue de fichier. Dans ce cas, la mise au point est remise au contrôle de modification et l’utilisateur doit continuer l’édition. L’implémentation par défaut affiche une boîte de messages indiquant à l’utilisateur le nom illégal du fichier et renvoie FALSE. Vous pouvez remplacer cette méthode, corriger le nom du fichier et retourner TRUE pour un traitement ultérieur.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
