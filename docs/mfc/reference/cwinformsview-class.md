---
title: CWinFormsView, classe
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369602"
---
# <a name="cwinformsview-class"></a>CWinFormsView, classe

Fournit les fonctionnalités génériques pour l'hébergement d'un contrôle Windows Forms en tant que vue MFC.

## <a name="syntax"></a>Syntaxe

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Construit un objet `CWinFormsView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Récupère un pointeur sur le contrôle des formulaires Windows.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom||
|----------|-|
|[CWinFormsView::contrôle de l’opérateur](#operator_control)|Lance un type comme pointeur vers un contrôle Windows Forms.|

## <a name="remarks"></a>Notes

MFC utilise `CWinFormsView` la classe pour héberger un contrôle .NET Framework Windows Forms dans une vue MFC. Le contrôle est un enfant de la vue autochtone et occupe toute la zone client de la vue MFC. Le résultat est `CFormView` similaire à une vue, vous permettant de profiter du concepteur de formulaires Windows et de courir le temps pour créer des vues basées sur la forme riche.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> L’intégration de MFC Windows Forms ne fonctionne que dans des projets qui se lient dynamiquement à MFC (projets dans lesquels AFXDLL est défini).

> [!NOTE]
> CWinFormsView ne prend pas en charge la fenêtre de splitter MFC ( [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)). Actuellement, seul le contrôle Windows Forms Splitter est pris en charge.

## <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinFormsView::CWinFormsView

Construit un objet `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Paramètres

*pManagedViewType*<br/>
Un pointeur sur le type de données du contrôle utilisateur windows Forms.

### <a name="example"></a>Exemple

Dans l’exemple `CUserView` suivant, la `CWinFormsView` classe hérite `UserControl1` et `CWinFormsView` passe le type de au constructeur. `UserControl1`est un contrôle sur mesure dans ControlLibrary.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinFormsView::GetControl

Récupère un pointeur sur le contrôle des formulaires Windows.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `System.Windows.Forms.Control`.

### <a name="remarks"></a>Notes

Pour un exemple de la façon d’utiliser les formulaires Windows, voir [à l’aide d’un contrôle utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinFormsView::contrôle de l’opérateur

Lance un type comme pointeur vers un contrôle Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Notes

Cet opérateur vous permet `CWinFormsView` de passer une vue sur les fonctions <xref:System.Windows.Forms.Control>qui acceptent un pointeur à un contrôle windows Forms de type .

### <a name="example"></a>Exemple

  Voir [CWinFormsView:GetControl](#getcontrol).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl, classe](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog, classe](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Classe CFormView](../../mfc/reference/cformview-class.md)
