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
ms.openlocfilehash: 99b4ff27a7686972bcbc85478998b52ed713ab5b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754259"
---
# <a name="ccolordialog-class"></a>CColorDialog, classe

Vous permet d’incorporer une boîte de dialogue de sélection de couleurs dans votre application.

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
|[CColorDialog::DoModal](#domodal)|Affiche une boîte de dialogue couleur et permet à l’utilisateur de faire une sélection.|
|[CColorDialog::GetColor](#getcolor)|Retourne `COLORREF` une structure contenant les valeurs de la couleur sélectionnée.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Récupère les couleurs personnalisées créées par l’utilisateur.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Force la sélection de couleurs actuelle à la couleur spécifiée.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Remplacement pour valider la couleur entrée dans la boîte de dialogue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Une structure utilisée pour personnaliser les paramètres de la boîte de dialogue.|

## <a name="remarks"></a>Notes

Un `CColorDialog` objet est une boîte de dialogue avec une liste de couleurs qui sont définies pour le système d’affichage. L’utilisateur peut sélectionner ou créer une couleur particulière de la liste, qui est ensuite rapportée à l’application lorsque la boîte de dialogue sort.

Pour construire `CColorDialog` un objet, utilisez le constructeur fourni ou dérivez une nouvelle classe et utilisez votre propre constructeur personnalisé.

Une fois que la boîte de dialogue a été construite, vous pouvez définir ou modifier toutes les valeurs de la structure [m_cc](#m_cc) pour initialiser les valeurs des commandes de la boîte de dialogue. La structure *m_cc* est de type [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1).

Après avoir paralysé les commandes `DoModal` de la boîte de dialogue, appelez la fonction du membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner une couleur. `DoModal`renvoie la sélection de l’utilisateur du bouton OK (IDOK) ou Annuler (IDCANCEL) de la boîte de dialogue.

Si `DoModal` vous retournez IDOK, `CColorDialog`vous pouvez utiliser l’une des fonctions des membres pour récupérer l’entrée d’informations par l’utilisateur.

Vous pouvez utiliser la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur.

`CColorDialog`s’appuie sur le COMMDLG. Fichier DLL qui expédie avec les versions Windows 3.1 et plus tard.

Pour personnaliser la boîte de dialogue, `CColorDialog`dérivez une classe, fournissez un modèle de dialogue personnalisé et ajoutez une carte de message pour traiter les messages de notification à partir des contrôles étendus. Tous les messages non traités doivent être transmis à la classe de base.

Personnaliser la fonction de crochet n’est pas nécessaire.

> [!NOTE]
> Sur certaines `CColorDialog` installations, l’objet ne s’affiche pas avec `CDialog` un fond gris si vous avez utilisé le cadre pour rendre d’autres objets gris.

Pour plus d’informations sur l’utilisation `CColorDialog`, voir Classes de dialogue [commun](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog::CColorDialog

Construit un objet `CColorDialog`.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*clrInit*<br/>
La sélection de couleurs par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RGB(0,0,0) (noir).

*dwFlags*<br/>
Un ensemble de drapeaux qui personnalisent la fonction et l’apparence de la boîte de dialogue. Pour plus d’informations, voir la structure [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1) dans le SDK Windows.

*pParentWnd*<br/>
Un pointeur à la fenêtre parent ou propriétaire de la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue couleur commune de Windows et permettre à l’utilisateur de sélectionner une couleur.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a choisi le bouton OK ou Annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différentes options de dialogue couleur-boîte en définissant les membres `DoModal` de la structure [m_cc,](#m_cc) vous devriez le faire avant d’appeler, mais après l’objet de dialogue-boîte est construit.

Après `DoModal`avoir appelé, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou l’entrée d’informations par l’utilisateur dans la boîte de dialogue.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CColorDialog:CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog::GetColor

Appelez cette fonction `DoModal` après avoir appelé pour récupérer les informations sur la couleur choisie par l’utilisateur.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui contient les informations RGB pour la couleur sélectionnée dans la boîte de dialogue couleur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`objets permettent à l’utilisateur, en plus de choisir des couleurs, de définir jusqu’à 16 couleurs personnalisées.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un tableau de 16 valeurs de couleur RGB qui stocke les couleurs personnalisées créées par l’utilisateur.

### <a name="remarks"></a>Notes

La `GetSavedCustomColors` fonction membre donne accès à ces couleurs. Ces couleurs peuvent être récupérées après [doModal](#domodal) retourne IDOK.

Chacune des 16 valeurs RGB dans le tableau retourné est parascée à RGB (255 255 255) (blanc). Les couleurs personnalisées choisies par l’utilisateur ne sont enregistrées qu’entre les invocations de la boîte de dialogue dans l’application. Si vous souhaitez enregistrer ces couleurs entre les invocations de l’application, vous devez les enregistrer d’une autre manière, comme dans une initialisation (. INI) fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog::m_cc

Une structure de type [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1), dont les membres stockent les caractéristiques et les valeurs de la boîte de dialogue.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Notes

Après la `CColorDialog` construction d’un objet, vous pouvez utiliser *m_cc* pour définir divers aspects de la boîte de dialogue avant d’appeler la fonction membre [DoModal.](#domodal)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::OnColorOK

Remplacement pour valider la couleur entrée dans la boîte de dialogue.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la boîte de dialogue ne doit pas être rejetée; sinon 0 pour accepter la couleur qui a été saisie.

### <a name="remarks"></a>Notes

Remplacer cette fonction uniquement si vous souhaitez fournir la validation personnalisée de la couleur que l’utilisateur sélectionne dans la boîte de dialogue couleur.

L’utilisateur peut sélectionner une couleur par l’une des deux méthodes suivantes :

- En cliquant sur une couleur sur la palette de couleurs. Les valeurs RGB de la couleur sélectionnée sont ensuite reflétées dans les boîtes d’édition RGB appropriées.

- Saisie des valeurs dans les boîtes d’édition RGB

La prépondérer `OnColorOK` vous permet de rejeter une couleur que l’utilisateur entre dans une boîte de dialogue couleur commune pour toute raison spécifique à l’application.

Normalement, vous n’avez pas besoin d’utiliser cette fonction parce que le cadre fournit la validation par défaut des couleurs et affiche une boîte de message si une couleur invalide est saisie.

Vous pouvez appeler [SetCurrentColor](#setcurrentcolor) de l’intérieur `OnColorOK` pour forcer une sélection de couleurs. Une `OnColorOK` fois a été tiré (c’est-à-dire, l’utilisateur clique **OK** pour accepter le changement de couleur), vous pouvez appeler [GetColor](#getcolor) pour obtenir la valeur RGB de la nouvelle couleur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Appelez cette fonction `DoModal` après avoir appelé pour forcer la sélection de couleur actuelle à la valeur de couleur spécifiée dans *clr*.

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Clr*<br/>
Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

Cette fonction est appelée à `OnColorOK`partir d’un gestionnaire de message ou . La boîte de dialogue mettra automatiquement à jour la sélection de l’utilisateur en fonction de la valeur du *paramètre clr.*

### <a name="example"></a>Exemple

  Voir l’exemple pour [CColorDialog:OnColorOK](#oncolorok).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
