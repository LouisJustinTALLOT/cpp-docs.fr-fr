---
title: Classe CMFCMaskedEdit
ms.date: 11/04/2016
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
ms.openlocfilehash: de28b308ec235e33e39aabd707677f4e75320b0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365279"
---
# <a name="cmfcmaskededit-class"></a>Classe CMFCMaskedEdit

La `CMFCMaskedEdit` classe prend en charge un contrôle d’édition masqué, qui valide l’entrée de l’utilisateur contre un masque et affiche les résultats validés selon un modèle.

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
|[CMFCMaskedEdit::DisableMask](#disablemask)|Désactiver la validation de l’entrée de l’utilisateur.|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Précise si la `GetWindowText` méthode ne récupère que des caractères masqués.|
|[CMFCMaskedEdit::EnableMask](#enablemask)|Initialise le contrôle masqué de modification.|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Précise si le contrôle d’édition masqué sélectionne des groupes particuliers d’entrée utilisateur, ou toutes les entrées de l’utilisateur.|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Précise si le texte est validé contre seulement des caractères masqués, ou contre l’ensemble du masque.|
|`CMFCMaskedEdit::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Récupère le texte validé du contrôle masqué de modification.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Spécifie une série de caractères valides que l’utilisateur peut entrer.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Affiche une invite dans le contrôle masqué de modification.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Appelé par le cadre pour valider le caractère spécifié par rapport au caractère de masque correspondant.|

## <a name="remarks"></a>Notes

Effectuez les étapes `CMFCMaskedEdit` suivantes pour utiliser le contrôle dans votre application :

1. Incorporer un `CMFCMaskedEdit` objet dans votre classe de fenêtre.

2. Appelez le [CMFCMaskedEdit::EnableMask](#enablemask) méthode pour spécifier le masque.

3. Appelez le [CMFCMaskedEdit::SetValidChars](#setvalidchars) méthode pour spécifier la liste des caractères valides.

4. Appelez le [CMFCMaskedEdit::SetWindowText](#setwindowtext) méthode pour spécifier le texte par défaut pour le contrôle de modification masquée.

5. Appelez le [CMFCMaskedEdit::GetWindowText](#getwindowtext) méthode pour récupérer le texte validé.

Si vous n’appelez pas une ou plusieurs méthodes pour initialiser le masque, les caractères valides et le texte par défaut, le contrôle masqué de modification se comporte au moment où le contrôle de modification standard se comporte.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un masque (par exemple `EnableMask` un numéro de téléphone) en utilisant `SetValidChars` la méthode pour créer le masque pour `SetWindowText` le contrôle masqué de modification, la méthode pour spécifier une chaîne de caractères valides que l’utilisateur peut entrer, et la méthode pour afficher une invite dans le contrôle masqué de modification. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxmaskededit.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFCMaskedEdit::DisableMask

Désactiver la validation de l’entrée de l’utilisateur.

```
void DisableMask();
```

### <a name="remarks"></a>Notes

Si la validation des entrées utilisateur est désactivée, le contrôle masqué de modification se comporte comme le contrôle standard de modification.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly

Précise si la `GetWindowText` méthode ne récupère que des caractères masqués.

```
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour spécifier que le [CMFCMaskedEdit::GetWindowText](#getwindowtext) méthode récupérer uniquement les caractères masqués; FALSE pour spécifier que la méthode récupère l’ensemble du texte. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour permettre la récupération de caractères masqués. Ensuite, créez un contrôle de modification masqué qui correspond au numéro de téléphone, tel que (425) 555-0187. Si vous `GetWindowText` appelez la méthode, elle renvoie "4255550187". Si vous désactivez les caractères `GetWindowText` masqués de récupération, la méthode renvoie le texte qui s’affiche dans le contrôle de modification, par exemple « (425) 555-0187 ».

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFCMaskedEdit::EnableMask

Initialise le contrôle masqué de modification.

```
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszMask (lpszMask)*<br/>
[dans] Une chaîne de masque qui spécifie le type de caractère qui peut apparaître à chaque position dans l’entrée de l’utilisateur. La longueur des chaînes de paramètres *lpszInputTemplate* et *lpszMask* doit être la même. Voir la section Remarques pour plus de détails sur les caractères masque.

*lpszInpoutemplate*<br/>
[dans] Une chaîne de modèle de masque qui spécifie les caractères littérals qui peuvent apparaître à chaque position dans l’entrée de l’utilisateur. Utilisez le caractère de soulignement (')comme lieu de caractère. La longueur des chaînes de paramètres *lpszInputTemplate* et *lpszMask* doit être la même.

*chMaskInpoutemplate*<br/>
[dans] Un caractère par défaut que le cadre remplace chaque personnage invalide dans l’entrée de l’utilisateur. La valeur par défaut de ce paramètre est soulignée ('').

*lpszValid (en)*<br/>
[dans] Une chaîne qui contient un ensemble de caractères valides. NULL indique que tous les caractères sont valides. La valeur par défaut de ce paramètre est NULL.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour créer le masque pour le contrôle masqué de modification. Dérivez une `CMFCMaskedEdit` classe de la classe et remplacez le [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) méthode d’utiliser votre propre code pour le traitement des masques personnalisés.

La liste de tableau suivante les caractères de masque par défaut :

|Caractère de masque|Définition|
|--------------------|----------------|
|D|Chiffre.|
|d|Chiffre ou espace.|
|+|Plus ('), moins ('-'), ou de l’espace.|
|C|Caractère alphabétique.|
|c|Caractère ou espace alphabétique.|
|Un|Caractère alphanumérique.|
|a|Caractère alphanumérique ou espace.|
|*|Un personnage imprimable.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup

Précise si le contrôle d’édition masqué permet à l’utilisateur de sélectionner des entrées de groupes particulières, ou toutes les entrées.

```
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour sélectionner seulement des groupes; FALSE pour sélectionner l’ensemble du texte. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour spécifier si le contrôle d’édition masqué permet à un utilisateur de sélectionner par groupe ou l’ensemble du texte.

Par défaut, la sélection par groupe est activée. Dans ce cas, l’utilisateur ne peut sélectionner que des groupes continus de caractères valides.

Par exemple, vous pouvez utiliser le contrôle de modification masqué suivant pour valider un numéro de téléphone :

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Si la sélection par groupe est activée, l’utilisateur ne peut récupérer que les groupes de cordes "425", "555" ou "0187". Si la sélection de groupe est désactivée, l’utilisateur peut récupérer l’intégralité du texte du numéro de téléphone : "(425) 555-0187".

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly

Précise si le texte est validé contre uniquement les personnages masqués, ou contre l’ensemble du masque.

```
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour valider l’entrée de l’utilisateur contre uniquement les caractères masqués; FALSE à valider contre l’ensemble du masque. La valeur par défaut est TRUE.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText

Récupère le texte validé du contrôle masqué de modification.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Paramètres

*lpszStringBuf*<br/>
[out] Un pointeur vers un tampon qui reçoit le texte du contrôle de modification.

*nMaxCount (en)*<br/>
[dans] Le nombre maximum de caractères à recevoir.

*rstrString (rstrString)*<br/>
[out] Une référence à l’objet de chaîne qui reçoit le texte du contrôle de modification.

### <a name="return-value"></a>Valeur de retour

La première surcharge de méthode renvoie le nombre d’octets de la chaîne qui est copié sur le paramètre *lpszStringBuf* tampon; 0 si le contrôle masqué de modification n’a pas de texte.

### <a name="remarks"></a>Notes

Cette méthode copie le texte du contrôle d’édition masqué au tampon *lpszStringBuf* ou à la chaîne *rstrString.*

Cette méthode redéfinit [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar

Appelé par le cadre pour valider le caractère spécifié par rapport au caractère de masque correspondant.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Paramètres

*chChar chChar*<br/>
[dans] Le personnage à valider.

*chMaskChar (en)*<br/>
[dans] Le caractère correspondant de la chaîne de masque.

### <a name="return-value"></a>Valeur de retour

VRAI si le paramètre *chChar* est le type de caractère autorisé par le paramètre *chMaskChar;* autrement, FALSE.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour valider les caractères d’entrée par vous-même. Pour plus d’informations sur les caractères de masque, voir la méthode [CMFCMaskedEdit::EnableMask](#enablemask) méthode.

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars

Spécifie une série de caractères valides que l’utilisateur peut entrer.

```
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszValid (en)*<br/>
[dans] Une chaîne qui contient l’ensemble des caractères d’entrée valides. NULL signifie que tous les caractères sont valides. La valeur par défaut de ce paramètre est NULL.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une liste de caractères valides. Si un personnage d’entrée n’est pas dans cette liste, le contrôle masqué de modification ne l’acceptera pas.

L’exemple de code suivant n’accepte que les nombres hexadecimal.

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText

Affiche une invite dans le contrôle masqué de modification.

```
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*lpszString (lpszString)*<br/>
[dans] Indique une corde non terminée qui sera utilisée comme invite.

### <a name="remarks"></a>Notes

Cette méthode définit le texte de contrôle.

Cette méthode redéfinit [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
