---
title: CColorDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: bc9bc76b328359d4c8ec7796de7dfaa7d3a9cf2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207722"
---
# <a name="ccolordialog-class"></a>CColorDialog, classe

Vous pouvez ainsi incorporer une boîte de dialogue de sélection de couleur dans votre application.

## <a name="syntax"></a>Syntaxe

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Construit un objet `CColorDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Affiche une boîte de dialogue couleur et autorise l’utilisateur à effectuer une sélection.|
|[CColorDialog::GetColor](#getcolor)|Retourne un `COLORREF` structure contenant les valeurs de la couleur sélectionnée.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Récupère les couleurs personnalisées créées par l’utilisateur.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Force la sélection de couleur actuelle à la couleur spécifiée.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Méthode override pour valider la couleur entrée dans la boîte de dialogue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Une structure utilisée pour personnaliser les paramètres de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Un `CColorDialog` objet est une boîte de dialogue avec une liste de couleurs qui sont définis pour le système d’affichage. L’utilisateur puisse sélectionner ou créer une couleur particulière à partir de la liste, qui est ensuite renvoyée à l’application lors de la boîte de dialogue se ferme.

Pour construire un `CColorDialog` de l’objet, utilisez le constructeur fourni ou dériver une nouvelle classe et utiliser votre propre constructeur personnalisé.

Une fois la boîte de dialogue a été construite, vous pouvez définir ou modifier des valeurs dans le [m_cc](#m_cc) structure pour initialiser les valeurs des contrôles de la boîte de dialogue. Le *m_cc* structure est de type [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora).

Après l’initialisation de contrôles de la boîte de dialogue, appelez le `DoModal` fonction membre pour afficher la boîte de dialogue et de permettre à l’utilisateur de sélectionner une couleur. `DoModal` Retourne la sélection de l’utilisateur du bouton OK (IDOK) ou Annuler (IDCANCEL) de la boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez utiliser une des `CColorDialog`de fonctions membres pour récupérer les informations entrées par l’utilisateur.

Vous pouvez utiliser le Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur.

`CColorDialog` s’appuie sur le COMMDLG. Fichier DLL qui est livré avec Windows 3.1 et versions ultérieures.

Pour personnaliser la boîte de dialogue, dérivez une classe de `CColorDialog`, de fournir un modèle de boîte de dialogue personnalisée et ajouter une table des messages pour traiter les messages de notification à partir de contrôles étendus. Tous les messages non traités doivent être passés à la classe de base.

Personnalisation de la fonction de raccordement n’est pas nécessaire.

> [!NOTE]
>  Sur certaines installations le `CColorDialog` objet n’affiche pas, avec un arrière-plan grisé, si vous avez utilisé le framework pour apporter d’autres `CDialog` gris d’objets.

Pour plus d’informations sur l’utilisation de `CColorDialog`, consultez [des Classes de boîte de dialogue communes](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog

Construit un objet `CColorDialog`.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*clrInit*<br/>
La sélection de couleur par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RGB(0,0,0) (noir).

*dwFlags*<br/>
Un jeu d’indicateurs qui personnalisent la fonction et l’apparence de la boîte de dialogue. Pour plus d’informations, consultez le [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora) structure dans le SDK Windows.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>  CColorDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue couleur Windows courants et permettre à l’utilisateur de sélectionner une couleur.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retournée, appelez le Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction permettant de déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou sur Annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différentes options de la boîte de dialogue couleur en définissant des membres de la [m_cc](#m_cc) structure, vous devez le faire avant d’appeler `DoModal` mais une fois que l’objet de la boîte de dialogue est construit.

Après avoir appelé `DoModal`, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CColorDialog::CColorDialog](#ccolordialog).

##  <a name="getcolor"></a>  CColorDialog::GetColor

Appelez cette fonction après l’appel `DoModal` pour extraire des informations sur la couleur sélectionnée par l’utilisateur.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui contient les informations de RVB pour la couleur sélectionnée dans la boîte de dialogue couleur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors

`CColorDialog` objets autorisent l’utilisateur, en plus de choisir les couleurs, définir des couleurs jusqu'à 16.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un tableau de valeurs de couleur RVB 16 qui stocke les couleurs personnalisées créées par l’utilisateur.

### <a name="remarks"></a>Notes

Le `GetSavedCustomColors` fonction membre permet d’accéder à ces couleurs. Ces couleurs peuvent être récupérées après [DoModal](#domodal) retourne IDOK.

Chacune des valeurs RVB 16 dans le tableau retourné est initialisée à RGB(255,255,255) (blanc). Les couleurs personnalisées sélectionnées par l’utilisateur sont enregistrés uniquement entre les appels de boîte de dialogue dans l’application. Si vous souhaitez enregistrer ces couleurs entre les appels de l’application, vous devez les enregistrer dans une autre manière, comme dans une initialisation (. Fichier INI).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

Une structure de type [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora), dont les membres stocker les caractéristiques et les valeurs de la boîte de dialogue.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CColorDialog` de l’objet, vous pouvez utiliser *m_cc* pour définir les divers aspects de la boîte de dialogue avant d’appeler le [DoModal](#domodal) fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>  CColorDialog::OnColorOK

Méthode override pour valider la couleur entrée dans la boîte de dialogue.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la boîte de dialogue ne doit pas être ignorée ; sinon 0 pour accepter la couleur qui a été entrée.

### <a name="remarks"></a>Notes

Remplacez cette fonction uniquement si vous souhaitez fournir une validation personnalisée de la couleur de que l’utilisateur sélectionne dans la boîte de dialogue couleur.

L’utilisateur peut sélectionner une couleur par une des deux méthodes suivantes :

- En cliquant sur une couleur dans la palette de couleurs. Les valeurs RVB de la couleur sélectionnée sont alors répercutées dans les zones d’édition RVB appropriées.

- Saisissez des valeurs dans le RVB zones d’édition

Substitution de `OnColorOK` vous permet de rejeter une couleur de l’utilisateur entre dans une boîte de dialogue de couleur pour une raison quelconque spécifique à l’application.

Normalement, vous n’avez pas besoin d’utiliser cette fonction, car le framework fournit la validation par défaut des couleurs et affiche un message si une couleur non valide est entrée.

Vous pouvez appeler [SetCurrentColor](#setcurrentcolor) depuis `OnColorOK` pour forcer une sélection de couleur. Une fois `OnColorOK` a été déclenché (autrement dit, l’utilisateur clique sur **OK** pour accepter la modification de couleur), vous pouvez appeler [GetColor](#getcolor) pour obtenir la valeur RVB de la nouvelle couleur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor

Appelez cette fonction après avoir appelé `DoModal` pour forcer la sélection de couleur actuelle à la valeur de couleur spécifiée dans *clr*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*clr*<br/>
Une valeur de couleur RVB.

### <a name="remarks"></a>Notes

Cette fonction est appelée dans un gestionnaire de messages ou `OnColorOK`. La boîte de dialogue met à jour automatiquement la sélection utilisateur en fonction de la valeur de la *clr* paramètre.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
