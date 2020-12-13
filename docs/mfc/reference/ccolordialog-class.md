---
description: 'En savoir plus sur : classe CColorDialog'
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
ms.openlocfilehash: d9af49d4986f0619211ed4fd2dc9174acea27d0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150135"
---
# <a name="ccolordialog-class"></a>CColorDialog, classe

Vous permet d’incorporer une boîte de dialogue de sélection de couleurs à votre application.

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
|[CColorDialog ::D oModal](#domodal)|Affiche une boîte de dialogue de couleur et permet à l’utilisateur d’effectuer une sélection.|
|[CColorDialog :: GetColor](#getcolor)|Retourne une `COLORREF` structure contenant les valeurs de la couleur sélectionnée.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Récupère les couleurs personnalisées créées par l’utilisateur.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Force la sélection de couleur actuelle à la couleur spécifiée.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Substituez pour valider la couleur entrée dans la boîte de dialogue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CColorDialog :: m_cc](#m_cc)|Structure utilisée pour personnaliser les paramètres de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Un `CColorDialog` objet est une boîte de dialogue avec une liste des couleurs définies pour le système d’affichage. L’utilisateur peut sélectionner ou créer une couleur particulière dans la liste, qui est ensuite renvoyée à l’application lorsque la boîte de dialogue s’arrête.

Pour construire un `CColorDialog` objet, utilisez le constructeur fourni ou dérivez une nouvelle classe et utilisez votre propre constructeur personnalisé.

Une fois la boîte de dialogue construite, vous pouvez définir ou modifier les valeurs de la structure [m_cc](#m_cc) pour initialiser les valeurs des contrôles de la boîte de dialogue. La structure *m_cc* est de type [les ChooseColor.](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1).

Après l’initialisation des contrôles de la boîte de dialogue, appelez la `DoModal` fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner une couleur. `DoModal` retourne la sélection de l’utilisateur du bouton OK (IDOK) ou CANCEL (IDCANCEL) de la boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez utiliser l’une des `CColorDialog` fonctions membres de pour récupérer les informations entrées par l’utilisateur.

Vous pouvez utiliser la fonction [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur.

`CColorDialog` s’appuie sur le fichier de COMMDLG.DLL fourni avec les versions de Windows 3,1 et ultérieures.

Pour personnaliser la boîte de dialogue, dérivez une classe de `CColorDialog` , fournissez un modèle de boîte de dialogue personnalisé et ajoutez une table des messages pour traiter les messages de notification des contrôles étendus. Tous les messages non traités doivent être passés à la classe de base.

La personnalisation de la fonction de raccordement n’est pas obligatoire.

> [!NOTE]
> Sur certaines installations `CColorDialog` , l’objet ne s’affiche pas avec un arrière-plan gris si vous avez utilisé l’infrastructure pour rendre d’autres `CDialog` objets en grisé.

Pour plus d’informations sur l’utilisation de `CColorDialog` , consultez [classes de boîtes de dialogue communes](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdlgs. h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a> CColorDialog::CColorDialog

Construit un objet `CColorDialog`.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*clrInit*<br/>
Sélection de couleur par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RVB (0, 0, 0) (noir).

*dwFlags*<br/>
Ensemble d’indicateurs qui personnalisent la fonction et l’apparence de la boîte de dialogue. Pour plus d’informations, consultez la structure [les ChooseColor.](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1) dans le SDK Windows.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a> CColorDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue couleur commune Windows et permettre à l’utilisateur de sélectionner une couleur.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différentes options de boîte de dialogue de couleur en définissant les membres de la structure [m_cc](#m_cc) , vous devez effectuer cette opération avant d’appeler, `DoModal` mais après la construction de l’objet de boîte de dialogue.

Après avoir appelé `DoModal` , vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations entrées par l’utilisateur dans la boîte de dialogue.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CColorDialog :: CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a> CColorDialog :: GetColor

Appelez cette fonction après avoir appelé `DoModal` pour récupérer les informations sur la couleur sélectionnée par l’utilisateur.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur [COLORREF](/windows/win32/gdi/colorref) qui contient les informations RVB de la couleur sélectionnée dans la boîte de dialogue couleur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a> CColorDialog::GetSavedCustomColors

`CColorDialog` les objets permettent à l’utilisateur, en plus de choisir des couleurs, de définir jusqu’à 16 couleurs personnalisées.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un tableau de 16 valeurs de couleur RVB qui stocke les couleurs personnalisées créées par l’utilisateur.

### <a name="remarks"></a>Notes

La `GetSavedCustomColors` fonction membre donne accès à ces couleurs. Ces couleurs peuvent être récupérées une fois que [DoModal](#domodal) retourne IDOK.

Chacune des 16 valeurs RVB dans le tableau retourné est initialisée à RGB (255255255) (blanc). Les couleurs personnalisées choisies par l’utilisateur sont enregistrées uniquement entre les appels de boîte de dialogue au sein de l’application. Si vous souhaitez enregistrer ces couleurs entre les appels de l’application, vous devez les enregistrer d’une autre manière, par exemple dans une initialisation (. INI).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a> CColorDialog :: m_cc

Structure de type [les ChooseColor.](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1), dont les membres stockent les caractéristiques et les valeurs de la boîte de dialogue.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CColorDialog` objet, vous pouvez utiliser *m_cc* pour définir différents aspects de la boîte de dialogue avant d’appeler la fonction membre [DoModal](#domodal) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a> CColorDialog::OnColorOK

Substituez pour valider la couleur entrée dans la boîte de dialogue.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si la boîte de dialogue ne doit pas être fermée. Sinon, 0 pour accepter la couleur qui a été entrée.

### <a name="remarks"></a>Notes

Substituez cette fonction uniquement si vous souhaitez fournir une validation personnalisée de la couleur sélectionnée par l’utilisateur dans la boîte de dialogue couleur.

L’utilisateur peut sélectionner une couleur à l’aide de l’une des deux méthodes suivantes :

- Cliquant sur une couleur de la palette de couleurs. Les valeurs RVB de la couleur sélectionnée sont ensuite reflétées dans les zones d’édition RVB appropriées.

- Saisie de valeurs dans les zones d’édition RVB

Le remplacement `OnColorOK` vous permet de rejeter une couleur entrée par l’utilisateur dans une boîte de dialogue de couleur commune pour toute raison spécifique à l’application.

Normalement, vous n’avez pas besoin d’utiliser cette fonction, car l’infrastructure fournit la validation par défaut des couleurs et affiche une boîte de message si une couleur non valide est entrée.

Vous pouvez appeler [SetCurrentColor](#setcurrentcolor) à partir de dans `OnColorOK` pour forcer une sélection de couleur. Une fois `OnColorOK` que a été déclenché (c’est-à-dire que l’utilisateur clique sur **OK** pour accepter la modification de couleur), vous pouvez appeler [GetColor](#getcolor) pour récupérer la valeur RVB de la nouvelle couleur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a> CColorDialog::SetCurrentColor

Appelez cette fonction après avoir appelé `DoModal` pour forcer la sélection de couleur actuelle à la valeur de couleur spécifiée dans *CLR*.

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Language*<br/>
Valeur de couleur RVB.

### <a name="remarks"></a>Notes

Cette fonction est appelée à partir d’un gestionnaire de messages ou `OnColorOK` . La boîte de dialogue met automatiquement à jour la sélection de l’utilisateur en fonction de la valeur du paramètre *CLR* .

### <a name="example"></a>Exemple

  Consultez l’exemple de [CColorDialog :: OnColorOK](#oncolorok).

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
