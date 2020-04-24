---
title: Mise en forme de CString et affichage des boîtes de message
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: fa1fe8826543834872de5257a0f5d56b2ad9fc1c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752672"
---
# <a name="cstring-formatting-and-message-box-display"></a>Mise en forme de CString et affichage des boîtes de message

Un certain nombre de fonctions sont `CString` fournies pour formater et analyser les objets. Vous pouvez utiliser ces fonctions `CString` chaque fois que vous devez manipuler des objets, mais elles sont particulièrement utiles pour formater les chaînes qui apparaîtront dans le texte de la boîte de message.

Ce groupe de fonctions comprend également une routine globale pour l’affichage d’une boîte de message.

### <a name="cstring-functions"></a>Fonctions CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrait des sous-cordes séparées par un seul caractère d’une chaîne source donnée.|
|[AfxFormatString1](#afxformatstring1)|Remplace une chaîne donnée pour les caractères format "%1" dans une chaîne contenue dans la table à cordes.|
|[AfxFormatString2](#afxformatstring2)|Remplace deux cordes pour les caractères format "%1" et "%2" dans une chaîne contenue dans la table à cordes.|
|[AfxMessageBox](#afxmessagebox)|Affiche une boîte de message.|

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString

Cette fonction globale peut être utilisée pour extraire un sous-corde à partir d’une chaîne source donnée.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Paramètres

*rString (en)*<br/>
Référence à un objet [CString](../../atl-mfc-shared/using-cstring.md) qui recevra un sous-corde individuel.

*lpszFullString*<br/>
Chaîne contenant le texte intégral de la chaîne à extraire.

*iSubString (en)*<br/>
Indice zéro de la sous-corde à extraire de *lpszFullString*.

*chSep (en)*<br/>
Caractère séparateur utilisé pour délimiter les sous-cordes.

### <a name="return-value"></a>Valeur de retour

VRAI si la fonction a réussi à extraire le sous-corde à l’indice fourni; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette fonction est utile pour extraire plusieurs sous-cordes à partir d’une chaîne source lorsqu’un personnage connu sépare chaque sous-corde. Cette fonction recherche depuis le début du paramètre *lpszFullString* chaque fois qu’il est appelé.

Cette fonction retournera FALSE si *lpszFullString* est réglé à NULL ou si la fonction atteint la fin de *lpszFullString* sans trouver *d’iSubString*no 1 occurrences du caractère séparateur spécifié. Le *paramètre rString* ne sera pas modifié à partir de sa valeur d’origine si *lpszFullString* a été réglé à NULL; autrement, le *paramètre rString* est réglé à la chaîne vide si le sous-corde ne pouvait pas être extrait pour l’index spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

Remplace la chaîne pointée par *lpsz1* pour tous les cas des caractères "%1" dans la ressource de chaîne de modèle identifiée par *nIDS*.

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Paramètres

*rString (en)*<br/>
Une référence `CString` à un objet qui contiendra la ficelle résultante après la substitution.

*nIDS (en)*<br/>
L’ID de ressource de la chaîne de modèle sur laquelle la substitution sera effectuée.

*lpsz1 (lpsz1)*<br/>
Une chaîne qui remplacera les caractères format "%1" dans la chaîne de modèle.

### <a name="remarks"></a>Notes

La nouvelle chaîne est stockée dans *rString*. Par exemple, si la chaîne dans le tableau de chaîne est "Fichier %1 non trouvé", et *lpsz1* est égal à "C: -MYFILE. TXT", puis *rString* contiendra la chaîne "File C:MYFILE. TXT n’a pas été trouvé". Cette fonction est utile pour formater les chaînes envoyées aux boîtes de messages et à d’autres fenêtres.

Si les caractères du format "%1" apparaissent dans la chaîne plus d’une fois, plusieurs substitutions seront effectuées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

Remplace la chaîne pointée par *lpsz1* pour tous les cas des caractères "%1", et la chaîne pointée par *lpsz2* pour tous les cas des caractères "%2", dans la ressource de chaîne de modèle identifiée par *nIDS*.

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Paramètres

*rString (en)*<br/>
Une référence `CString` à celle qui contiendra la ficelle résultante après la substitution.

*nIDS (en)*<br/>
L’ID de table de chaîne de la chaîne de modèle sur laquelle la substitution sera effectuée.

*lpsz1 (lpsz1)*<br/>
Une chaîne qui remplacera les caractères format "%1" dans la chaîne de modèle.

*lpsz2 (lpsz2)*<br/>
Une chaîne qui remplacera les caractères format "%2" dans la chaîne de modèle.

### <a name="remarks"></a>Notes

La nouvelle chaîne est stockée dans *rString*. Par exemple, si la chaîne dans le tableau de chaîne est "File %1 ne trouve pas dans l’annuaire %2", *lpsz1* pointe à "MYFILE. TXT", et *lpsz2* pointe à "C:MYDIR", puis *rString* contiendra la chaîne "File MYFILE. TXT ne trouve pas dans l’annuaire C: -MYDIR"

Si les caractères de format "%1" ou "%2" apparaissent dans la chaîne plus d’une fois, plusieurs substitutions seront faites. Ils n’ont pas besoin d’être en ordre numérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox AfxMessageBox

Affiche une boîte de message sur l’écran.

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Points vers `CString` un objet ou une corde non terminée contenant le message à afficher dans la boîte à messages.

*nType*<br/>
Le style de la boîte à messages. Appliquez n’importe lequel des [styles de boîte de message](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) à la boîte.

*nIDHelp (en)*<br/>
L’ID de contexte d’aide pour le message ; 0 indique que le contexte par défaut de l’application Sera utilisé.

*nIDPrompt (en)*<br/>
Un ID unique utilisé pour référencer une chaîne dans la table à cordes.

### <a name="return-value"></a>Valeur de retour

Zéro s’il n’y a pas assez de mémoire pour afficher la boîte de message; autrement, l’une des valeurs suivantes est retournée :

- IDABORT Le bouton Abort a été sélectionné.

- IDCANCEL Le bouton Annuler a été sélectionné.

- IDIGNORE Le bouton Ignorer a été sélectionné.

- IDNO Le bouton No a été sélectionné.

- IDOK Le bouton OK a été sélectionné.

- IDRETRY Le bouton Retry a été sélectionné.

- IDYES Le bouton Oui a été sélectionné.

Si une boîte de message a un bouton Annuler, la valeur IDCANCEL sera retournée si la clé ESC est pressée ou si le bouton Annuler est sélectionné. Si la boîte de message n’a pas de bouton Annuler, appuyer sur la touche ESC n’a aucun effet.

Les fonctions [AfxFormatString1](#afxformatstring1) et [AfxFormatString2](#afxformatstring2) peuvent être utiles pour formater le texte qui apparaît dans une boîte de message.

### <a name="remarks"></a>Notes

La première forme de cette fonction surchargée affiche une chaîne de texte pointée par *lpszText* dans la boîte de message et utilise *nIDHelp* pour décrire un contexte d’aide. Le contexte d’aide est utilisé pour sauter à un sujet d’aide associé lorsque l’utilisateur appuie sur la clé d’aide (généralement F1).

La deuxième forme de la fonction utilise la ressource de chaîne avec l’ID *nIDPrompt* pour afficher un message dans la boîte de message. La page d’aide associée se trouve à travers la valeur de *nIDHelp*. Si la valeur par défaut de *nIDHelp* est utilisée (-1), l’ID de ressources de chaîne, *nIDPrompt*, est utilisé pour le contexte d’aide. Pour plus d’informations sur la définition des contextes d’aide, voir [Note technique 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md)
