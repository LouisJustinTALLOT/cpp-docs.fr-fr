---
title: Cmfceditbrowsectrl, classe
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
ms.openlocfilehash: 0c6fb39e17e22bcac60d50b87f7370c6a9f91db9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770676"
---
# <a name="cmfceditbrowsectrl-class"></a>Cmfceditbrowsectrl, classe

Le `CMFCEditBrowseCtrl` classe prend en charge le contrôle de navigation d’édition, qui est une zone de texte modifiable contenant éventuellement un bouton Parcourir. Lorsque l’utilisateur clique sur le bouton Parcourir, le contrôle effectue une action personnalisée ou affiche une boîte de dialogue standard qui contient un explorateur de fichiers ou de dossiers.

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
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Active ou désactive (masque) le bouton Parcourir.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Active le bouton Parcourir et place du contrôle de navigation de modification dans *parcourir les fichiers* mode.|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Active le bouton Parcourir et place du contrôle de navigation de modification dans *parcourir les dossiers* mode.|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Retourne le mode de navigation en cours.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Appelé par l’infrastructure après que le contrôle edit est mis à jour avec le résultat d’une action de navigation.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Appelé par l’infrastructure une fois que l’utilisateur clique sur le bouton Parcourir.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Redessine le contrôle de navigation d’édition actuel.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Appelé par l’infrastructure pour dessiner le bouton Parcourir.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Appelé par le framework lorsqu’un nom de fichier non conforme a été entré dans le contrôle d’édition.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) des fonctions de Windows. Pour la syntaxe et plus d’informations, consultez [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Définit une image personnalisée pour le bouton Parcourir.|

## <a name="remarks"></a>Notes

Utiliser un contrôle d’édition Parcourir pour sélectionner un nom de fichier ou dossier. Si vous le souhaitez, utiliser le contrôle pour effectuer une action personnalisée comme pour afficher une boîte de dialogue. Vous pouvez afficher ou pas le bouton Parcourir, et vous pouvez appliquer une étiquette personnalisée ou une image sur le bouton.

Le *en mode de navigation* du modifier pour parcourir le contrôle détermine s’il affiche un bouton Parcourir et action qui se produit lorsque le bouton est activé. Pour plus d’informations, consultez le [GetMode](#getmode) (méthode).

Le `CMFCEditBrowseCtrl` classe prend en charge les modes suivants.

- **mode personnalisé**

   Une action personnalisée est effectuée lorsque l’utilisateur clique sur le bouton Parcourir. Par exemple, vous pouvez afficher une boîte de dialogue spécifique à l’application.

- **mode de fichier**

   Une boîte de dialogue de sélection de fichier standard s’affiche lorsque l’utilisateur clique sur le bouton Parcourir.

- **mode dossier**

   Une boîte de dialogue de sélection de dossier standard s’affiche lorsque l’utilisateur clique sur le bouton Parcourir.

## <a name="how-to-specify-an-edit-browse-control"></a>Guide pratique : Spécifier un contrôle d’édition Parcourir

Procédez comme suit pour incorporer un contrôle d’édition Parcourir dans votre application :

1. Si vous souhaitez implémenter un mode de navigation personnalisés, dérivez votre propre classe à partir de la `CMFCEditBrowseCtrl` classe, puis vous remplacez le [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) (méthode). Dans la méthode substituée, exécuter une action Parcourir personnalisée et mettre à jour le contrôle d’édition parcourir avec le résultat.

1. Soit incorporer la `CMFCEditBrowseCtrl` objet ou l’objet de contrôle de recherche de modification dérivée dans l’objet de fenêtre parent.

1. Si vous utilisez le **Assistant classe** pour créer une boîte de dialogue, ajoutez un contrôle d’édition ( `CEdit`) pour le formulaire de boîte de dialogue. En outre, ajoutez une variable pour accéder au contrôle dans votre fichier d’en-tête. Dans votre fichier d’en-tête, modifiez le type de la variable de `CEdit` à `CMFCEditBrowseCtrl`. Le contrôle edit est créé automatiquement. Si vous n’utilisez pas le **Assistant classe**, ajoutez un `CMFCEditBrowseCtrl` variable et votre fichier d’en-tête puis appelez ses `Create` (méthode).

1. Si vous ajoutez un contrôle de navigation d’édition à une boîte de dialogue, utilisez le **ClassWizard** outil pour configurer l’échange de données.

1. Appelez le [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), ou [EnableBrowseButton](#enablebrowsebutton) méthode pour définir le mode de navigation et d’afficher le bouton Parcourir. Appelez le [GetMode](#getmode) méthode pour obtenir le mode de navigation en cours.

1. Pour fournir une image personnalisée pour le bouton Parcourir, appelez le [SetBrowseButtonImage](#setbrowsebuttonimage) méthode ou remplacement le [OnDrawBrowseButton](#ondrawbrowsebutton) (méthode).

1. Pour supprimer le bouton Parcourir à partir du contrôle de navigation de modification, appelez le [EnableBrowseButton](#enablebrowsebutton) méthode avec le *bActivez* paramètre défini sur FALSE.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser deux méthodes dans le `CMFCEditBrowseCtrl` classe : `EnableFolderBrowseButton` et `EnableFileBrowseButton`. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** afxeditbrowsectrl.h

##  <a name="enablebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableBrowseButton

Affiche ou n’affiche pas le bouton Parcourir sur le contrôle de navigation d’édition actuel.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
True pour afficher le bouton Parcourir ; FALSE à ne pas afficher le bouton Parcourir. La valeur par défaut est TRUE.

*szLabel*<br/>
L’étiquette qui s’affiche sur le bouton Parcourir. La valeur par défaut est « **...** ".

### <a name="remarks"></a>Notes

Si le *bActivez* paramètre a la valeur TRUE, implémenter une action personnalisée pour effectuer un clic sur le bouton Parcourir. Pour implémenter une action personnalisée, dérivez une classe de la `CMFCEditBrowseCtrl` classe, puis vous remplacez son [OnBrowse](#onbrowse) (méthode).

Si le *bActivez* paramètre a la valeur TRUE, le mode de navigation du contrôle est `BrowseMode_Default`; sinon, le mode de navigation est `BrowseMode_None`. Pour plus d’informations sur les modes de navigation, consultez le [GetMode](#getmode) (méthode).

##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton

Affiche le bouton Parcourir sur le contrôle de navigation d’édition actuel et place le contrôle dans *parcourir les fichiers* mode.

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Paramètres

*lpszDefExt*<br/>
Spécifie l’extension de nom de fichier par défaut utilisée dans la boîte de dialogue de sélection de fichier. La valeur par défaut est NULL.

*lpszFilter*<br/>
Spécifie la chaîne de filtrage par défaut utilisée dans la boîte de dialogue de sélection de fichier. La valeur par défaut est NULL.

*dwFlags*<br/>
Indicateurs de boîte de dialogue. La valeur par défaut est une combinaison (OR) au niveau du bit de OFN_HIDEREADONLY et OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Notes

Quand le contrôle de zone de modification est en mode de navigation de fichiers et que l'utilisateur clique sur le bouton parcourir, le contrôle affiche la boîte de dialogue de sélection de fichier standard.

Pour obtenir une liste complète des indicateurs disponibles, consultez [structure OPENFILENAME](/windows/desktop/api/commdlg/ns-commdlg-tagofna).

##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton

Affiche le bouton Parcourir sur le contrôle de navigation d’édition actuel et place le contrôle dans *parcourir les dossiers* mode.

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Notes

Lorsque le contrôle de navigation d’édition est en mode de navigation de dossier et l’utilisateur clique sur le bouton Parcourir, le contrôle affiche la boîte de dialogue de sélection de dossier standard.

##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode

Récupère le mode de navigation du contrôle de navigation d’édition actuel.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Valeur de retour

Une des valeurs d’énumération qui spécifie le mode actuel de la modification parcourir le contrôle. Le mode de navigation détermine si l’infrastructure affiche le bouton Parcourir et quelle action se produit lorsqu’un utilisateur clique sur ce bouton.

Le tableau ci-dessous répertorie les valeurs de retour possibles.

|Value|Description|
|-----------|-----------------|
|`BrowseMode_Default`|**mode personnalisé**. Une action définie par le programmeur est effectuée.|
|`BrowseMode_File`|**mode de fichier**. La boîte de dialogue de navigateur de fichier standard s’affiche.|
|`BrowseMode_Folder`|**mode dossier**. La boîte de dialogue du navigateur dossier standard s’affiche.|
|`BrowseMode_None`|Le bouton Parcourir n’est pas affiché.|

### <a name="remarks"></a>Notes

Par défaut, un `CMFCEditBrowseCtrl` objet est initialisé à `BrowseMode_None` mode. Modifier le mode de navigation avec le [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), et [CMFCEditBrowseCtrl::EnableFolderBrowseButton ](#enablefolderbrowsebutton) méthodes.

##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate

Appelé par l’infrastructure après que le contrôle edit est mis à jour avec le résultat d’une action de navigation.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter une action personnalisée.

##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse

Appelé par l’infrastructure une fois que l’utilisateur clique sur le bouton Parcourir du contrôle d’édition Parcourir.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Notes

Cette méthode permet d’exécuter du code personnalisé lorsque l’utilisateur clique sur le bouton Parcourir du contrôle d’édition Parcourir. Dérivez votre propre classe de la `CMFCEditBrowseCtrl` classe et substituer sa `OnBrowse` (méthode). Dans cette méthode, implémentez une action Parcourir personnalisée et éventuellement mettre à jour la zone de texte du contrôle d’édition Parcourir. Dans votre application, utilisez le [EnableBrowseButton](#enablebrowsebutton) méthode permettant de placer le contrôle d’édition Parcourir *Parcourir personnalisée* mode.

##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout

Redessine le contrôle de navigation d’édition actuel.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsque le mode de navigation du modifier, accédez contrôle change. Pour plus d’informations, consultez [CMFCEditBrowseCtrl::GetMode](#getmode).

##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton

Appelé par l’infrastructure pour dessiner le bouton Parcourir sur le contrôle d’édition Parcourir.

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
Le rectangle englobant du bouton Parcourir.

*bIsButtonPressed*<br/>
TRUE si le bouton est enfoncé ; Sinon, FALSE.

*bIsButtonHot*<br/>
TRUE si le bouton est mis en surbrillance ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Remplacez cette fonction dans une classe dérivée pour personnaliser l’apparence du bouton Parcourir.

##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage

Définit une image personnalisée sur le bouton Parcourir du contrôle d’édition Parcourir.

```
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>Paramètres

*hIcon*<br/>
Le handle d’une icône.

*hBitmap*<br/>
Le handle d’une image bitmap.

*uiBmpResId*<br/>
L’ID de ressource d’une image bitmap.

*bAutoDestroy*<br/>
TRUE pour supprimer l’icône spécifiée ou bitmap lorsque cette méthode se termine ; Sinon, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour appliquer une image personnalisée pour le bouton Parcourir. Par défaut, le framework Obtient une image standard lorsque le contrôle edit est dans *parcourir les fichiers* ou *parcourir les dossiers* mode.

##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName

Appelé par le framework lorsqu’un nom de fichier non conforme a été entré dans le contrôle d’édition.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Paramètres

*strFileName*<br/>
Spécifie le nom de fichier non conforme.

### <a name="return-value"></a>Valeur de retour

Retournera FALSE si ce nom de fichier ne peut pas être transmis à la suite de la boîte de dialogue de fichier. Dans ce cas, le focus est redéfini pour le contrôle d’édition et l’utilisateur doit continuer à modifier. L’implémentation par défaut affiche une boîte de message qui informe l’utilisateur sur le nom de fichier non conforme et retourne FALSE. Vous pouvez substituer cette méthode, veuillez corriger le nom de fichier et renvoie la valeur TRUE pour un traitement ultérieur.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
