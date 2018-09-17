---
title: Cusertool, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 577e4b4e7bf54742035c8b4333d345ca894501ac
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708992"
---
# <a name="cusertool-class"></a>Cusertool, classe
Un outil utilisateur est un élément de menu qui exécute une application externe. Le **outils** onglet de la **personnaliser** boîte de dialogue ( [cmfctoolbarscustomizedialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) permet à l’utilisateur d’ajouter des outils de l’utilisateur et pour spécifier le nom, les commandes, les arguments, et répertoire initial de chaque outil utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|Dessine l’icône d’outil de l’utilisateur dans un rectangle spécifié.|  
|[CUserTool::GetCommand](#getcommand)|Retourne une chaîne qui contienne le texte de la commande associée à l’outil utilisateur.|  
|[CUserTool::GetCommandId](#getcommandid)|Retourne l’ID de commande de l’élément de menu de l’outil utilisateur.|  
|[CUserTool::Invoke](#invoke)|Exécute la commande associée à l’outil utilisateur.|  
|[CUserTool::Serialize](#serialize)|Lit ou écrit cet objet dans une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CUserTool::SetCommand](#setcommand)|Définit la commande associée à l’outil utilisateur.|  
|[CUserTool::SetToolIcon](#settoolicon)|Charge l’icône de l’outil de l’utilisateur à partir de l’application associée à l’outil.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Charge l’icône par défaut pour un outil utilisateur.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|Les arguments de ligne de commande pour l’outil utilisateur.|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Le répertoire initial pour l’outil utilisateur.|  
|[CUserTool::m_strLabel](#m_strlabel)|Le nom de l’outil qui est affiché dans l’élément de menu pour l’outil.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur l’activation des outils de l’utilisateur dans votre application, consultez [cusertoolsmanager, classe](../../mfc/reference/cusertoolsmanager-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un outil à partir d’un `CUserToolsManager` de l’objet, définissez le `m_strLabel` variable de membre et définissez l’application qui exécute l’outil utilisateur. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard  
 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon  
 Dessine l’icône d’outil de l’utilisateur dans le centre d’un rectangle spécifié.  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers un contexte de périphérique.  
  
*rectImage*<br/>
[in] Spécifie les coordonnées de la zone pour afficher l’icône.  
  
##  <a name="getcommand"></a>  CUserTool::GetCommand  
 Retourne une chaîne qui contienne le texte de la commande associée à l’outil utilisateur.  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à `CString` objet qui contient le texte de la commande associée à l’outil utilisateur.  
  
##  <a name="getcommandid"></a>  CUserTool::GetCommandId  
 Retourne l’ID de commande de l’outil utilisateur.  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de commande de cet outil utilisateur.  
  
##  <a name="invoke"></a>  CUserTool::Invoke  
 Exécute la commande associée à l’outil utilisateur.  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la commande a été exécutée avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Appels [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) pour exécuter une commande associée à l’outil utilisateur. La fonction échoue si la commande est vide ou si [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) échoue.  
  
##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon  
 Charge l’icône par défaut pour un outil utilisateur.  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers l’icône chargé (HICON), ou NULL si l’icône par défaut ne peut pas être chargé.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’il est impossible de charger une icône pour un outil défini par l’utilisateur à partir du fichier exécutable de l’outil.  
  
 Substituez cette méthode pour fournir votre propre icône de l’outil par défaut.  
  
##  <a name="m_strarguments"></a>  CUserTool::m_strArguments  
 Les arguments de ligne de commande pour l’outil utilisateur.  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>Notes  
 Cette chaîne est passée à l’outil lorsque vous appelez [CUserTool::Invoke](#invoke) ou quand un utilisateur clique sur la commande associée à cet outil.  
  
##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory  
 Spécifie le répertoire initial pour l’outil utilisateur.  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>Notes  
 Cette variable Spécifie le répertoire initial qui l’outil s’exécute dans lorsque vous appelez [CUserTool::Invoke](#invoke) ou quand un utilisateur clique sur la commande associée à cet outil.  
  
##  <a name="m_strlabel"></a>  CUserTool::m_strLabel  
 L’étiquette est affichée dans l’élément de menu pour l’outil.  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>  CUserTool::Serialize  
 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *ar*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setcommand"></a>  CUserTool::SetCommand  
 Définit l’application qui exécute l’outil utilisateur.  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>Paramètres  
*lpszCmd*<br/>
[in] Spécifie la nouvelle application à associer à l’outil utilisateur.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour définir une nouvelle application qui exécute l’outil utilisateur. La méthode détruit l’icône ancien et charge une nouvelle icône de l’application donnée. Si elle ne peut pas charger une icône à partir de l’application, il charge l’icône par défaut pour un outil utilisateur en appelant [CUserTool::LoadDefaultIcon](#loaddefaulticon).  
  
##  <a name="settoolicon"></a>  CUserTool::SetToolIcon  
 Charge l’icône de l’outil de l’utilisateur à partir de l’application qui utilise l’outil.  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers l’icône chargé.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour charger l’icône à afficher sur l’élément de menu. Cette méthode recherche l’icône dans le fichier exécutable qui utilise l’outil. Si elle n’a pas d’une icône par défaut, l’icône fournie par [CUserTool::LoadDefaultIcon](#loaddefaulticon) est utilisé à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager, classe](../../mfc/reference/cusertoolsmanager-class.md)
