---
title: Classe de CMFCMaskedEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
dev_langs:
- C++
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 985cd4011dbb1ea8ccad7cd40c81833dd5507f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371795"
---
# <a name="cmfcmaskededit-class"></a>Classe de CMFCMaskedEdit
La `CMFCMaskedEdit` classe prend en charge un contrôle d’édition par masque, ce qui valide l’entrée d’utilisateur par rapport à un masque et affiche les résultats validés en fonction d’un modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|Constructeur par défaut.|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|Désactive la validation des entrées utilisateur.|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Spécifie si le `GetWindowText` méthode récupère uniquement les caractères masqués.|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|Contrôle d’édition initialise le texte masqué.|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Spécifie si le contrôle d’édition par masque sélectionne des groupes d’entrée d’utilisateur, ou toutes les entrées utilisateur.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Spécifie si le texte est validé par rapport uniquement masqué caractères, ou pour le masque entier.|  
|`CMFCMaskedEdit::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Récupère de valider le texte du contrôle d’édition par masque.|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Spécifie une chaîne de caractères valides que l’utilisateur peut entrer.|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Affiche une invite dans le contrôle d’édition par masque.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Appelé par le framework pour valider le caractère spécifié par rapport à caractère masque correspondant.|  
  
## <a name="remarks"></a>Notes  
 Procédez comme suit pour utiliser le `CMFCMaskedEdit` contrôle dans votre application :  
  
 1. Incorporer une `CMFCMaskedEdit` objet dans votre classe de fenêtre.  
  
 2. Appelez le [CMFCMaskedEdit::EnableMask](#enablemask) méthode pour spécifier le masque.  
  
 3. Appelez le [CMFCMaskedEdit::SetValidChars](#setvalidchars) méthode pour spécifier la liste des caractères valides.  
  
 4. Appelez le [CMFCMaskedEdit::SetWindowText](#setwindowtext) méthode pour spécifier le texte par défaut pour le contrôle d’édition du texte masqué.  
  
 5. Appelez le [CMFCMaskedEdit::GetWindowText](#getwindowtext) méthode pour récupérer le texte validé.  
  
 Si vous n’appelez pas une ou plusieurs méthodes pour initialiser le masque, des caractères valides et le texte par défaut, le contrôle d’édition par masque se comporte uniquement comme le contrôle d’édition standard.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir un masque (par exemple un numéro de téléphone) à l’aide de la `EnableMask` méthode pour créer le masque pour modifier le contrôle, le texte masqué le `SetValidChars` pour spécifier une chaîne de caractères valides que l’utilisateur peut entrer et (méthode)`SetWindowText` contrôle d’édition de méthode pour afficher une invite de commandes dans le texte masqué. Cet exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxmaskededit.h  
  
##  <a name="disablemask"></a>  CMFCMaskedEdit::DisableMask  
 Désactive la validation des entrées utilisateur.  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>Notes  
 Si la validation des entrées d’utilisateur est désactivée, le contrôle d’édition par masque se comporte comme la norme de contrôle d’édition.  
  
##  <a name="enablegetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 Spécifie si le `GetWindowText` méthode récupère uniquement les caractères masqués.  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour spécifier que le [CMFCMaskedEdit::GetWindowText](#getwindowtext) méthode récupérer masqué uniquement des caractères ; `FALSE` pour spécifier que la méthode de récupérer l’intégralité du texte. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour permettre la récupération des caractères masqués. Ensuite, créez un contrôle d’édition par masque qui correspond au numéro de téléphone, tels que (425) 555-0187. Si vous appelez le `GetWindowText` (méthode), elle retourne « 4255550187 ». Si vous désactivez la récupération des caractères masqués, le `GetWindowText` méthode retourne le texte qui s’affiche dans le contrôle d’édition, par exemple « (425) 555-0187 ».  
  
##  <a name="enablemask"></a>  CMFCMaskedEdit::EnableMask  
 Contrôle d’édition initialise le texte masqué.  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszMask`  
 Chaîne de masque qui spécifie le type de caractère qui peut apparaître à chaque position dans l’entrée d’utilisateur. La longueur de la `lpszInputTemplate` et `lpszMask` chaînes de paramètres doivent être identiques. Consultez la section Notes pour plus de détails sur les caractères de masque.  
  
 [in] `lpszInputTemplate`  
 Une chaîne de modèle de masque qui indique le littéral de caractères qui peut apparaître à chaque position dans l’entrée d’utilisateur. Utiliser le caractère de soulignement (« _ ») comme un espace réservé de caractère. La longueur de la `lpszInputTemplate` et `lpszMask` chaînes de paramètres doivent être identiques.  
  
 [in] `chMaskInputTemplate`  
 Un caractère par défaut que le framework remplace chaque caractère non valide dans l’entrée d’utilisateur. La valeur par défaut de ce paramètre est un trait de soulignement (« _ »).  
  
 [in] `lpszValid`  
 Chaîne qui contient un jeu de caractères valides. `NULL` Indique que tous les caractères sont valides. La valeur par défaut de ce paramètre est `NULL`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour créer le masque pour le contrôle d’édition par masque. Dérivez une classe de la `CMFCMaskedEdit` classe et substituer les [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) méthode à utiliser votre propre code pour le traitement de masque personnalisé.  
  
 Le tableau suivant répertorie les caractères de masque par défaut :  
  
|Caractère de masque|Définition|  
|--------------------|----------------|  
|D|Chiffre.|  
|d|Chiffre ou espace.|  
|+|Plus (« + »), moins («- »), ou l’espace.|  
|C|Caractère alphabétique.|  
|c|Caractère alphabétique ou un espace.|  
|A|Caractère alphanumérique.|  
|a|Caractère alphanumérique ou espace.|  
|*|Un caractère imprimable.|  
  
##  <a name="enableselectbygroup"></a>  CMFCMaskedEdit::EnableSelectByGroup  
 Spécifie si le contrôle d’édition par masque permet à l’utilisateur à l’entrée de sélectionner des groupes particulier, ou toutes les entrées.  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour sélectionner uniquement des groupes ; `FALSE` pour sélectionner l’intégralité du texte. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet de spécifier si le contrôle d’édition par masque permet à un utilisateur de sélectionner par groupe ou l’intégralité du texte.  
  
 Par défaut, la sélection par groupe est activée. Dans ce cas, l’utilisateur peut sélectionner uniquement les groupes continues de caractères valides.  
  
 Par exemple, vous pouvez utiliser le contrôle d’édition par masque suivant pour valider un numéro de téléphone :  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 Si la sélection par groupe est activée, l’utilisateur peut récupérer uniquement les « 425 », « 555 » ou les groupes de chaîne de « 0187 ». Si la sélection de groupe est désactivée. l’utilisateur peut récupérer du texte entier du numéro de téléphone : « (425) 555-0187 ».  
  
##  <a name="enablesetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 Spécifie si le texte est validé par rapport aux seuls les caractères masqués, ou par rapport au masque entier.  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour valider l’utilisateur par rapport à masqué uniquement des caractères ; `FALSE` pour la validation du masque entier. La valeur par défaut est `TRUE`.  
  
##  <a name="getwindowtext"></a>  CMFCMaskedEdit::GetWindowText  
 Récupère de valider le texte du contrôle d’édition par masque.  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `lpszStringBuf`  
 Pointeur vers une mémoire tampon qui reçoit le texte dans le contrôle d’édition.  
  
 [in] `nMaxCount`  
 Le nombre maximal de caractères à recevoir.  
  
 [out] `rstrString`  
 Une référence à l’objet de chaîne qui reçoit le texte dans le contrôle d’édition.  
  
### <a name="return-value"></a>Valeur de retour  
 La première surcharge de méthode retourne le nombre d’octets de la chaîne qui est copié vers le `lpszStringBuf` mémoire tampon de paramètre ; 0 si le contrôle d’édition par masque ne comporte pas de texte.  
  
### <a name="remarks"></a>Notes  
 Cette méthode copie le texte du contrôle d’édition par masque à la `lpszStringBuf` tampon ou `rstrString` chaîne.  
  
 Cette méthode redéfinit [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).  
  
##  <a name="ismaskedchar"></a>  CMFCMaskedEdit::IsMaskedChar  
 Appelé par le framework pour valider le caractère spécifié par rapport à caractère masque correspondant.  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `chChar`  
 Caractère à valider.  
  
 [in] `chMaskChar`  
 Le caractère correspondant de la chaîne de masque.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le `chChar` paramètre est le type de caractères autorisé par le `chMaskChar` paramètre ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour valider les caractères d’entrée à votre rythme. Pour plus d’informations sur les caractères de masque, consultez le [CMFCMaskedEdit::EnableMask](#enablemask) (méthode).  
  
##  <a name="setvalidchars"></a>  CMFCMaskedEdit::SetValidChars  
 Spécifie une chaîne de caractères valides que l’utilisateur peut entrer.  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszValid`  
 Chaîne qui contient le jeu de caractères d’entrée valides. `NULL` signifie que tous les caractères sont valides. La valeur par défaut de ce paramètre est `NULL`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir une liste de caractères valides. Si un caractère d’entrée n’est pas dans cette liste, contrôle d’édition par masque l’acceptera pas.  
  
 L’exemple de code suivant accepte uniquement les nombres hexadécimaux.  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>  CMFCMaskedEdit::SetWindowText  
 Affiche une invite dans le contrôle d’édition par masque.  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszString`  
 Pointe vers une chaîne se terminant par null qui sera utilisé comme une invite de commandes.  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit le texte du contrôle.  
  
 Cette méthode redéfinit [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CEdit, classe](../../mfc/reference/cedit-class.md)
