---
title: CUserTool, classe
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: 203adeac9783da8ea49a8385dad9786865c8a225
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373217"
---
# <a name="cusertool-class"></a>CUserTool, classe

Un outil utilisateur est un élément de menu qui exécute une application externe. **L’onglet Outils** de la boîte de dialogue **Customize** [(CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) permet à l’utilisateur d’ajouter des outils utilisateur et de spécifier le nom, la commande, les arguments et l’annuaire initial pour chaque outil utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CUserTool : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Dessine l’icône de l’outil utilisateur dans un rectangle spécifié.|
|[CUserTool::GetCommand](#getcommand)|Retourne une chaîne qui contient le texte de la commande associée à l’outil utilisateur.|
|[CUserTool::GetCommandId](#getcommandid)|Retourne l’ID de commande de l’élément de menu de l’outil utilisateur.|
|[CUserTool::Invoquer](#invoke)|Exécute la commande associée à l’outil utilisateur.|
|[CUserTool::Serialize](#serialize)|Lit ou écrit cet objet dans une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Définit la commande associée à l’outil utilisateur.|
|[CUserTool::SetToolIcon](#settoolicon)|Charge l’icône pour l’outil utilisateur de l’application associée à l’outil.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Charge l’icône par défaut pour un outil utilisateur.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Les arguments de commande-ligne pour l’outil d’utilisateur.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|L’annuaire initial de l’outil utilisateur.|
|[CUserTool::m_strLabel](#m_strlabel)|Le nom de l’outil qui est affiché dans l’élément de menu pour l’outil.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la façon d’activer les outils utilisateur de votre application, consultez [la classe CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer `CUserToolsManager` un outil `m_strLabel` à partir d’un objet, définir la variable du membre et définir l’application que l’outil utilisateur exécute. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>CUserTool::DrawToolIcon

Dessine l’icône de l’outil utilisateur au centre d’un rectangle spécifié.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectImage*<br/>
[dans] Spécifie les coordonnées de la zone pour afficher l’icône.

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>CUserTool::GetCommand

Retourne une chaîne qui contient le texte de la commande associée à l’outil utilisateur.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence `CString` à l’objet qui contient le texte de la commande associée à l’outil utilisateur.

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>CUserTool::GetCommandId

Renvoie l’ID de commande de l’outil utilisateur.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Valeur de retour

L’ID de commande de cet outil utilisateur.

## <a name="cusertoolinvoke"></a><a name="invoke"></a>CUserTool::Invoquer

Exécute la commande associée à l’outil utilisateur.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la commande a été exécutée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Appelle [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) pour exécuter une commande associée à l’outil utilisateur. La fonction échoue si la commande est vide ou si [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) échoue.

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

Charge l’icône par défaut pour un outil utilisateur.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Valeur de retour

Une poignée à l’icône chargée ( HICON), ou NULL si l’icône par défaut ne peut pas être chargée.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’elle est incapable de charger une icône pour un outil défini par l’utilisateur à partir du fichier exécutable de l’outil.

Remplacez cette méthode pour fournir votre propre icône d’outil par défaut.

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>CUserTool::m_strArguments

Les arguments de commande-ligne pour l’outil d’utilisateur.

```
CString m_strArguments;
```

### <a name="remarks"></a>Notes

Cette chaîne est transmise à l’outil lorsque vous appelez [CUserTool::Invoke](#invoke) ou quand un utilisateur clique sur la commande associée à cet outil.

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

Spécifie l’annuaire initial de l’outil utilisateur.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Notes

Cette variable spécifie l’annuaire initial dans lequel l’outil exécute lorsque vous appelez [CUserTool::Invoke](#invoke) ou quand un utilisateur clique sur la commande associée à cet outil.

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>CUserTool::m_strLabel

L’étiquette qui est affichée dans l’élément de menu pour l’outil.

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>CUserTool::Serialize

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

[dans] *ar*<br/>

### <a name="remarks"></a>Notes

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>CUserTool::SetCommand

Définit l’application que l’outil utilisateur exécute.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Paramètres

*lpszCmd (en)*<br/>
[dans] Spécifie la nouvelle application à associer à l’outil utilisateur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir une nouvelle application que l’outil utilisateur exécute. La méthode détruit l’ancienne icône et charge une nouvelle icône de l’application donnée. S’il ne peut pas charger une icône de l’application, il charge l’icône par défaut pour un outil utilisateur en appelant [CUserTool::LoadDefaultIcon](#loaddefaulticon).

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>CUserTool::SetToolIcon

Charge l’icône pour l’outil utilisateur de l’application que l’outil utilise.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Valeur de retour

Une poignée à l’icône chargée.

### <a name="remarks"></a>Notes

Appelez cette méthode pour charger l’icône à afficher sur l’élément de menu. Cette méthode recherche l’icône dans le fichier exécutable que l’outil utilise. S’il n’a pas d’icône par défaut, l’icône fournie par [CUserTool ::LoadDefaultIcon](#loaddefaulticon) est utilisée à la place.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)<br/>
[Classe CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
