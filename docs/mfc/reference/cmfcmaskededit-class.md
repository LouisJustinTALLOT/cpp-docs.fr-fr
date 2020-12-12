---
description: 'En savoir plus sur : classe CMFCMaskedEdit'
title: CMFCMaskedEdit, classe
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
ms.openlocfilehash: 7ac61240e2941eafbbac3cbb03a4884e282cbca3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265153"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit, classe

La `CMFCMaskedEdit` classe prend en charge un contrôle d’édition masqué qui valide l’entrée utilisateur par rapport à un masque et affiche les résultats validés en fonction d’un modèle.

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
|[CMFCMaskedEdit ::D isableMask](#disablemask)|Désactive la validation des entrées d’utilisateur.|
|[CMFCMaskedEdit :: EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Spécifie si la `GetWindowText` méthode récupère uniquement les caractères masqués.|
|[CMFCMaskedEdit :: EnableMask](#enablemask)|Initialise le contrôle d’édition masqué.|
|[CMFCMaskedEdit :: EnableSelectByGroup](#enableselectbygroup)|Spécifie si le contrôle d’édition masqué sélectionne des groupes particuliers d’entrées d’utilisateur ou toutes les entrées d’utilisateur.|
|[CMFCMaskedEdit :: EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Spécifie si le texte est validé par rapport uniquement aux caractères masqués, ou par rapport au masque entier.|
|`CMFCMaskedEdit::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCMaskedEdit :: GetWindowText](#getwindowtext)|Récupère le texte validé à partir du contrôle d’édition masqué.|
|[CMFCMaskedEdit :: SetValidChars](#setvalidchars)|Spécifie une chaîne de caractères valides que l’utilisateur peut entrer.|
|[CMFCMaskedEdit :: SetWindowText](#setwindowtext)|Affiche une invite dans le contrôle d’édition masqué.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCMaskedEdit :: IsMaskedChar](#ismaskedchar)|Appelé par l’infrastructure pour valider le caractère spécifié par rapport au caractère de masque correspondant.|

## <a name="remarks"></a>Notes

Pour utiliser le `CMFCMaskedEdit` contrôle dans votre application, procédez comme suit :

1. Incorporez un `CMFCMaskedEdit` objet dans la classe de fenêtre.

2. Appelez la méthode [CMFCMaskedEdit :: EnableMask](#enablemask) pour spécifier le masque.

3. Appelez la méthode [CMFCMaskedEdit :: SetValidChars](#setvalidchars) pour spécifier la liste des caractères valides.

4. Appelez la méthode [CMFCMaskedEdit :: SetWindowText](#setwindowtext) pour spécifier le texte par défaut du contrôle d’édition masqué.

5. Appelez la méthode [CMFCMaskedEdit :: GetWindowText](#getwindowtext) pour récupérer le texte validé.

Si vous n’appelez pas une ou plusieurs méthodes pour initialiser le masque, les caractères valides et le texte par défaut, le contrôle d’édition masqué se comporte de la même façon que le contrôle d’édition standard.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un masque (par exemple, un numéro de téléphone) à l’aide de la `EnableMask` méthode pour créer le masque pour le contrôle d’édition masqué, la `SetValidChars` méthode pour spécifier une chaîne de caractères valides que l’utilisateur peut entrer, et la `SetWindowText` méthode pour afficher une invite dans le contrôle d’édition masqué. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxmaskededit. h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a> CMFCMaskedEdit ::D isableMask

Désactive la validation des entrées d’utilisateur.

```cpp
void DisableMask();
```

### <a name="remarks"></a>Notes

Si la validation des entrées de l’utilisateur est désactivée, le contrôle d’édition masqué se comporte comme le contrôle d’édition standard.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a> CMFCMaskedEdit :: EnableGetMaskedCharsOnly

Spécifie si la `GetWindowText` méthode récupère uniquement les caractères masqués.

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour spécifier que la méthode [CMFCMaskedEdit :: GetWindowText](#getwindowtext) récupère uniquement les caractères masqués ; FALSe pour spécifier que la méthode récupère l’ensemble du texte. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour activer la récupération de caractères masqués. Créez ensuite un contrôle d’édition masqué qui correspond au numéro de téléphone, par exemple (425) 555-0187. Si vous appelez la `GetWindowText` méthode, elle retourne « 4255550187 ». Si vous désactivez la récupération de caractères masqués, la `GetWindowText` méthode retourne le texte affiché dans le contrôle d’édition, par exemple « (425) 555-0187 ».

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a> CMFCMaskedEdit :: EnableMask

Initialise le contrôle d’édition masqué.

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszMask*<br/>
dans Chaîne de masque qui spécifie le type de caractère qui peut apparaître à chaque position dans l’entrée d’utilisateur. La longueur des chaînes de paramètres *lpszInputTemplate* et *lpszMask* doit être identique. Consultez la section Notes pour plus d’informations sur les caractères de masque.

*lpszInputTemplate*<br/>
dans Chaîne de modèle de masque qui spécifie les caractères littéraux qui peuvent apparaître à chaque position dans l’entrée d’utilisateur. Utilisez le trait de soulignement (« _ ») comme espace réservé de caractère. La longueur des chaînes de paramètres *lpszInputTemplate* et *lpszMask* doit être identique.

*chMaskInputTemplate*<br/>
dans Caractère par défaut que l’infrastructure remplace pour chaque caractère non valide dans l’entrée d’utilisateur. La valeur par défaut de ce paramètre est trait de soulignement (« _ »).

*lpszValid*<br/>
dans Chaîne qui contient un jeu de caractères valides. La valeur NULL indique que tous les caractères sont valides. La valeur par défaut de ce paramètre est NULL.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour créer le masque pour le contrôle d’édition masqué. Dérivez une classe de la `CMFCMaskedEdit` classe et substituez la méthode [CMFCMaskedEdit :: IsMaskedChar](#ismaskedchar) pour utiliser votre propre code pour le traitement de masque personnalisé.

Le tableau suivant répertorie les caractères de masque par défaut :

|Caractère de masque|Définition|
|--------------------|----------------|
|D|Caractères.|
|d|Chiffre ou espace.|
|+|Plus (« + »), moins (« - ») ou espace.|
|C|Caractère alphabétique.|
|c|Caractère alphabétique ou espace.|
|Un|Caractère alphanumérique.|
|a|Caractère alphanumérique ou espace.|
|*|Caractère imprimable.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a> CMFCMaskedEdit :: EnableSelectByGroup

Spécifie si le contrôle d’édition masqué permet à l’utilisateur de sélectionner une entrée de groupes particuliers, ou toute entrée.

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour sélectionner uniquement les groupes ; FALSe pour sélectionner l’intégralité du texte. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour spécifier si le contrôle d’édition masqué permet à un utilisateur de sélectionner par groupe ou par le texte entier.

Par défaut, la sélection par groupe est activée. Dans ce cas, l’utilisateur peut sélectionner uniquement des groupes continus de caractères valides.

Par exemple, vous pouvez utiliser le contrôle d’édition masqué suivant pour valider un numéro de téléphone :

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Si la sélection par groupe est activée, l’utilisateur peut récupérer uniquement les groupes de chaînes « 425 », « 555 » ou « 0187 ». Si la sélection de groupe est désactivée, l’utilisateur peut récupérer le texte entier du numéro de téléphone : « (425) 555-0187 ».

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a> CMFCMaskedEdit :: EnableSetMaskedCharsOnly

Spécifie si le texte est validé par rapport uniquement aux caractères masqués, ou par rapport au masque entier.

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour valider l’entrée utilisateur par rapport aux caractères masqués uniquement ; FALSe pour effectuer une validation par rapport au masque entier. La valeur par défaut est TRUE.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a> CMFCMaskedEdit :: GetWindowText

Récupère le texte validé à partir du contrôle d’édition masqué.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Paramètres

*lpszStringBuf*<br/>
à Pointeur vers une mémoire tampon qui reçoit le texte du contrôle d’édition.

*nMaxCount*<br/>
dans Nombre maximal de caractères à recevoir.

*rstrString*<br/>
à Référence à l’objet String qui reçoit le texte du contrôle d’édition.

### <a name="return-value"></a>Valeur renvoyée

La première surcharge de méthode retourne le nombre d’octets de la chaîne copiée dans la mémoire tampon de paramètre *lpszStringBuf* ; 0 si le contrôle d’édition masqué n’a pas de texte.

### <a name="remarks"></a>Notes

Cette méthode copie le texte du contrôle d’édition masqué vers la mémoire tampon *lpszStringBuf* ou la chaîne *rstrString* .

Cette méthode redéfinit [CWnd :: GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a> CMFCMaskedEdit :: IsMaskedChar

Appelé par l’infrastructure pour valider le caractère spécifié par rapport au caractère de masque correspondant.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Paramètres

*chChar*<br/>
dans Caractère à valider.

*chMaskChar*<br/>
dans Caractère correspondant de la chaîne de masque.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le paramètre *chChar* est le type de caractère autorisé par le paramètre *chMaskChar* ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Substituez cette méthode pour valider vos propres caractères d’entrée. Pour plus d’informations sur les caractères de masque, consultez la méthode [CMFCMaskedEdit :: EnableMask](#enablemask) .

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a> CMFCMaskedEdit :: SetValidChars

Spécifie une chaîne de caractères valides que l’utilisateur peut entrer.

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszValid*<br/>
dans Chaîne qui contient le jeu de caractères d’entrée valides. NULL signifie que tous les caractères sont valides. La valeur par défaut de ce paramètre est NULL.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une liste de caractères valides. Si un caractère d’entrée ne figure pas dans cette liste, le contrôle d’édition masqué n’accepte pas ce caractère.

L’exemple de code suivant accepte uniquement les nombres hexadécimaux.

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

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a> CMFCMaskedEdit :: SetWindowText

Affiche une invite dans le contrôle d’édition masqué.

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*lpszString*<br/>
dans Pointe vers une chaîne se terminant par un caractère null qui sera utilisée comme invite.

### <a name="remarks"></a>Notes

Cette méthode définit le texte du contrôle.

Cette méthode redéfinit [CWnd :: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)
