---
description: 'En savoir plus sur : classe CMFCEditBrowseCtrl'
title: CMFCEditBrowseCtrl, classe
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
ms.openlocfilehash: f63ab87207678cca87db84b73e49fba571634f3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293889"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl, classe

La `CMFCEditBrowseCtrl` classe prend en charge le contrôle Edit Browse, qui est une zone de texte modifiable qui contient éventuellement un bouton Parcourir. Lorsque l’utilisateur clique sur le bouton Parcourir, le contrôle effectue une action personnalisée ou affiche une boîte de dialogue standard qui contient un explorateur de fichiers ou de dossiers.

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
|[CMFCEditBrowseCtrl :: EnableBrowseButton](#enablebrowsebutton)|Active ou désactive (masque) le bouton Parcourir.|
|[CMFCEditBrowseCtrl :: EnableFileBrowseButton](#enablefilebrowsebutton)|Active le bouton Parcourir et place le contrôle Edit Browse en mode de navigation dans les *fichiers* .|
|[CMFCEditBrowseCtrl :: EnableFolderBrowseButton](#enablefolderbrowsebutton)|Active le bouton Parcourir et met le contrôle Edit Browse en mode de navigation dans les *dossiers* .|
|[CMFCEditBrowseCtrl :: GetMode](#getmode)|Retourne le mode de navigation actuel.|
|[CMFCEditBrowseCtrl :: OnAfterUpdate](#onafterupdate)|Appelée par le Framework après que le contrôle Edit Browse a été mis à jour avec le résultat d’une action Browse.|
|[CMFCEditBrowseCtrl :: OnBrowse](#onbrowse)|Appelée par l’infrastructure après que l’utilisateur a cliqué sur le bouton Parcourir.|
|[CMFCEditBrowseCtrl :: OnChangeLayout](#onchangelayout)|Redessine le contrôle d’exploration de la modification en cours.|
|[CMFCEditBrowseCtrl :: OnDrawBrowseButton](#ondrawbrowsebutton)|Appelé par l’infrastructure pour dessiner le bouton Parcourir.|
|[CMFCEditBrowseCtrl :: OnIllegalFileName](#onillegalfilename)|Appelé par le Framework lorsqu’un nom de fichier non conforme a été entré dans le contrôle d’édition.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Pour plus d’informations sur la syntaxe et plus d’informations, consultez [CWnd ::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl :: SetBrowseButtonImage](#setbrowsebuttonimage)|Définit une image personnalisée pour le bouton Parcourir.|

## <a name="remarks"></a>Notes

Utilisez un contrôle Edit Browse pour sélectionner un nom de fichier ou de dossier. Le cas échéant, utilisez le contrôle pour effectuer une action personnalisée telle que pour afficher une boîte de dialogue. Vous pouvez afficher ou ne pas afficher le bouton Parcourir, et vous pouvez appliquer une étiquette ou une image personnalisée sur le bouton.

Le *mode de navigation* du contrôle Edit Browse détermine s’il affiche un bouton Parcourir et l’action qui se produit lorsque l’utilisateur clique sur le bouton. Pour plus d’informations, consultez la méthode [GetMode](#getmode) .

La `CMFCEditBrowseCtrl` classe prend en charge les modes suivants.

- **mode personnalisé**

   Une action personnalisée est exécutée lorsque l’utilisateur clique sur le bouton Parcourir. Par exemple, vous pouvez afficher une boîte de dialogue spécifique à l’application.

- **mode de fichier**

   Une boîte de dialogue de sélection de fichier standard s’affiche lorsque l’utilisateur clique sur le bouton Parcourir.

- **mode dossier**

   Une boîte de dialogue de sélection de dossier standard s’affiche lorsque l’utilisateur clique sur le bouton Parcourir.

## <a name="how-to-specify-an-edit-browse-control"></a>Comment : spécifier un contrôle Edit Browse

Pour incorporer un contrôle Edit Browse dans votre application, procédez comme suit :

1. Si vous souhaitez implémenter un mode de navigation personnalisé, dérivez votre propre classe de la `CMFCEditBrowseCtrl` classe, puis substituez la méthode [CMFCEditBrowseCtrl :: OnBrowse](#onbrowse) . Dans la méthode substituée, exécutez une action Browse personnalisée et mettez à jour le contrôle Edit Browse avec le résultat.

1. Incorporez l’objet `CMFCEditBrowseCtrl` ou l’objet de contrôle Edit Browse dérivé dans l’objet de fenêtre parente.

1. Si vous utilisez l' **Assistant classe** pour créer une boîte de dialogue, ajoutez un contrôle d’édition ( `CEdit` ) au formulaire de boîte de dialogue. En outre, ajoutez une variable pour accéder au contrôle dans votre fichier d’en-tête. Dans votre fichier d’en-tête, remplacez le type de la variable par `CEdit` `CMFCEditBrowseCtrl` . Le contrôle Edit Browse est créé automatiquement. Si vous n’utilisez pas l' **Assistant classe**, ajoutez une `CMFCEditBrowseCtrl` variable à votre fichier d’en-tête, puis appelez sa `Create` méthode.

1. Si vous ajoutez un contrôle Edit Browse à une boîte de dialogue, utilisez l’outil **ClassWizard** pour configurer l’échange de données.

1. Appelez la méthode [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)ou [EnableBrowseButton](#enablebrowsebutton) pour définir le mode de navigation et afficher le bouton Parcourir. Appelez la méthode [GetMode](#getmode) pour obtenir le mode de navigation actuel.

1. Pour fournir une image personnalisée pour le bouton Parcourir, appelez la méthode [SetBrowseButtonImage](#setbrowsebuttonimage) ou remplacez la méthode [OnDrawBrowseButton](#ondrawbrowsebutton) .

1. Pour supprimer le bouton Parcourir du contrôle Edit Browse, appelez la méthode [EnableBrowseButton](#enablebrowsebutton) avec le paramètre *BENABLE* défini sur false.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser deux méthodes dans la `CMFCEditBrowseCtrl` classe : `EnableFolderBrowseButton` et `EnableFileBrowseButton` . Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** afxeditbrowsectrl. h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a> CMFCEditBrowseCtrl :: EnableBrowseButton

Affiche ou n’affiche pas le bouton Parcourir sur le contrôle Edit Browse actuel.

```cpp
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
TRUE pour afficher le bouton Parcourir ; FALSe pour ne pas afficher le bouton Parcourir. La valeur par défaut est TRUE.

*szLabel*<br/>
Étiquette affichée sur le bouton Parcourir. La valeur par défaut est « **...**».

### <a name="remarks"></a>Notes

Si le paramètre *bEnable* a la valeur true, implémentez une action personnalisée à effectuer lorsque l’utilisateur clique sur le bouton Parcourir. Pour implémenter une action personnalisée, dérivez une classe de la `CMFCEditBrowseCtrl` classe, puis substituez sa méthode [OnBrowse](#onbrowse) .

Si le paramètre *bEnable* a la valeur true, le mode de navigation du contrôle est `BrowseMode_Default` ; sinon, le mode de navigation est `BrowseMode_None` . Pour plus d’informations sur les modes de navigation, consultez la méthode [GetMode](#getmode) .

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a> CMFCEditBrowseCtrl :: EnableFileBrowseButton

Affiche le bouton Parcourir sur le contrôle Edit Browse actuel et place le contrôle en mode de navigation dans les *fichiers* .

```cpp
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

Pour obtenir la liste complète des indicateurs disponibles, consultez la rubrique de la [structure OpenFileName](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a> CMFCEditBrowseCtrl :: EnableFolderBrowseButton

Affiche le bouton Parcourir sur le contrôle Edit Browse actuel et place le contrôle en mode de navigation dans les *dossiers* .

```cpp
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Notes

Quand le contrôle Edit Browse est en mode de navigation dans les dossiers et que l’utilisateur clique sur le bouton Parcourir, le contrôle affiche la boîte de dialogue de sélection de dossier standard.

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a> CMFCEditBrowseCtrl :: GetMode

Récupère le mode de navigation du contrôle Edit Browse actuel.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs d’énumération qui spécifie le mode actuel du contrôle d’exploration de la modification. Le mode de navigation détermine si le Framework affiche le bouton Parcourir et l’action qui se produit lorsqu’un utilisateur clique sur ce bouton.

Le tableau ci-dessous répertorie les valeurs de retour possibles.

|Valeur|Description|
|-----------|-----------------|
|`BrowseMode_Default`|**mode personnalisé**. Une action définie par le programmeur est effectuée.|
|`BrowseMode_File`|**mode de fichier**. La boîte de dialogue standard de l’Explorateur de fichiers s’affiche.|
|`BrowseMode_Folder`|**mode dossier**. La boîte de dialogue Explorateur de dossiers standard s’affiche.|
|`BrowseMode_None`|Le bouton Parcourir n’est pas affiché.|

### <a name="remarks"></a>Notes

Par défaut, un `CMFCEditBrowseCtrl` objet est initialisé en `BrowseMode_None` mode. Modifiez le mode de navigation avec les méthodes [CMFCEditBrowseCtrl :: EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl :: EnableFileBrowseButton](#enablefilebrowsebutton)et [CMFCEditBrowseCtrl :: EnableFolderBrowseButton](#enablefolderbrowsebutton) .

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a> CMFCEditBrowseCtrl :: OnAfterUpdate

Appelée par le Framework après que le contrôle Edit Browse a été mis à jour avec le résultat d’une action Browse.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour implémenter une action personnalisée.

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a> CMFCEditBrowseCtrl :: OnBrowse

Appelée par l’infrastructure après que l’utilisateur a cliqué sur le bouton Parcourir du contrôle Edit Browse.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Notes

Utilisez cette méthode pour exécuter du code personnalisé lorsque l’utilisateur clique sur le bouton Parcourir du contrôle Edit Browse. Dérivez votre propre classe de la `CMFCEditBrowseCtrl` classe et substituez sa `OnBrowse` méthode. Dans cette méthode, implémentez une action Browse personnalisée et mettez éventuellement à jour la zone de texte du contrôle Edit Browse. Dans votre application, utilisez la méthode [EnableBrowseButton](#enablebrowsebutton) pour placer le contrôle Edit Browse en mode de *navigation personnalisé* .

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a> CMFCEditBrowseCtrl :: OnChangeLayout

Redessine le contrôle d’exploration de la modification en cours.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsque le mode de navigation du contrôle Edit Browse change. Pour plus d’informations, consultez [CMFCEditBrowseCtrl :: GetMode](#getmode).

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a> CMFCEditBrowseCtrl :: OnDrawBrowseButton

Appelé par l’infrastructure pour dessiner le bouton Parcourir sur le contrôle Edit Browse.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers un contexte de périphérique.

*Rect*<br/>
Rectangle englobant du bouton Parcourir.

*bIsButtonPressed*<br/>
TRUE si le bouton est enfoncé ; Sinon, FALSe.

*bIsButtonHot*<br/>
TRUE si le bouton est mis en surbrillance ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Substituez cette fonction dans une classe dérivée pour personnaliser l’apparence du bouton Parcourir.

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a> CMFCEditBrowseCtrl :: SetBrowseButtonImage

Définit une image personnalisée sur le bouton Parcourir du contrôle Edit Browse.

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

*hIcon*<br/>
Handle d’une icône.

*hBitmap*<br/>
Handle d’une bitmap.

*uiBmpResId*<br/>
ID de ressource d’une image bitmap.

*bAutoDestroy*<br/>
TRUE pour supprimer l’icône ou la bitmap spécifiée lorsque cette méthode se termine ; Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour appliquer une image personnalisée au bouton Parcourir. Par défaut, le Framework obtient une image standard lorsque le contrôle modifier la navigation est en mode de *recherche de fichiers* ou de navigation dans les *dossiers* .

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a> CMFCEditBrowseCtrl :: OnIllegalFileName

Appelé par le Framework lorsqu’un nom de fichier non conforme a été entré dans le contrôle d’édition.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Paramètres

*strFileName*<br/>
Spécifie le nom de fichier non conforme.

### <a name="return-value"></a>Valeur renvoyée

Doit retourner FALSe si ce nom de fichier ne peut pas être passé plus loin dans la boîte de dialogue de fichier. Dans ce cas, le focus est rétabli sur le contrôle Edit et l’utilisateur doit poursuivre la modification. L’implémentation par défaut affiche une boîte de message indiquant à l’utilisateur le nom de fichier non conforme et retourne FALSe. Vous pouvez substituer cette méthode, corriger le nom de fichier et retourner la valeur TRUE pour un traitement supplémentaire.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
