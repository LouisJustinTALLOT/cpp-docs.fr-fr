---
title: Mise en forme de CString et affichage des boîtes de message
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.strings
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: fee8ba89605e6425b511407dab62be1f32e94a9d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272644"
---
# <a name="cstring-formatting-and-message-box-display"></a>Mise en forme de CString et affichage des boîtes de message

Un nombre de fonctions est fourni pour mettre en forme et analyser `CString` objets. Vous pouvez utiliser ces fonctions chaque fois que vous devez manipuler `CString` objets, mais ils sont particulièrement utiles pour la mise en forme de chaînes qui s’affichent dans le texte de la boîte de message.

Ce groupe de fonctions inclut également une routine globale pour afficher une boîte de message.

### <a name="cstring-functions"></a>Fonctions de CString

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extraire des sous-chaînes séparés par un caractère unique à partir d’une chaîne source donnée.|
|[AfxFormatString1](#afxformatstring1)|Remplace une chaîne donnée pour les caractères de format « %1 » dans une chaîne contenue dans la table de chaînes.|
|[AfxFormatString2](#afxformatstring2)|Chaînes de substituts deux pour le format de caractères « %1 » et « %2 » dans une chaîne contenue dans la table de chaînes.|
|[AfxMessageBox](#afxmessagebox)|Affiche une boîte de message.|

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

##  <a name="afxextractsubstring"></a>  AfxExtractSubString

Cette fonction globale peut être utilisée pour extraire une sous-chaîne d’une chaîne source donnée.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Référence à un [CString](../../atl-mfc-shared/using-cstring.md) objet qui recevra une sous-chaîne individuelle.

*lpszFullString*<br/>
Chaîne contenant le texte complet de la chaîne à extraire.

*iSubString*<br/>
Index de base zéro de la sous-chaîne à extraire *lpszFullString*.

*chSep*<br/>
Caractère de séparation utilisé pour délimiter les sous-chaînes.

### <a name="return-value"></a>Valeur de retour

TRUE si la fonction extraction réussie de la sous-chaîne à l’index fourni ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette fonction est utile lors de l’extraction plusieurs sous-chaînes d’une chaîne source un caractère unique connu sépare chaque sous-chaîne. Cette fonction recherche à partir du début de la *lpszFullString* paramètre chaque fois qu’elle est appelée.

Cette fonction retourne FALSE si *lpszFullString* est définie sur NULL ou la fonction atteint la fin de *lpszFullString* sans recherche *iSubString*+ 1 occurrences du caractère séparateur spécifié. Le *rString* paramètre ne sera pas modifié à partir de sa valeur d’origine si *lpszFullString* a été défini à NULL ; sinon, le *rString* paramètre est défini sur une chaîne vide si la sous-chaîne n’a pas pu être extrait pour l’index spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

Remplace la chaîne vers laquelle pointée *lpsz1* pour toutes les instances des caractères « %1 » de la ressource de chaîne de modèle identifié par *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Une référence à un `CString` objet qui contient la chaîne résultante après la substitution est effectuée.

*nIDS*<br/>
L’ID de ressource de la chaîne de modèle sur lequel la substitution sera effectuée.

*lpsz1*<br/>
Chaîne qui remplace le format de caractères « %1 » dans la chaîne de modèle.

### <a name="remarks"></a>Notes

La chaîne qui vient d’être formée est stockée dans *rString*. Par exemple, si la chaîne dans la table de chaînes est « Fichier %1 introuvable », et *lpsz1* est égal à « C:\MYFILE. TXT », puis *rString* contient la chaîne « fichier C:\MYFILE. TXT introuvable ». Cette fonction est utile pour mettre en forme de chaînes envoyées à des boîtes de message et les autres fenêtres.

Si les caractères de format « %1 » apparaissent plusieurs fois dans la chaîne, sera plusieurs substitutions.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

Remplace la chaîne vers laquelle pointée *lpsz1* pour toutes les instances des caractères « %1 » et la chaîne vers laquelle pointe *lpsz2* pour toutes les instances des caractères « %2 », dans la ressource de chaîne de modèle identifié par *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Une référence à la `CString` qui contient la chaîne résultante après la substitution est effectuée.

*nIDS*<br/>
L’ID de table de chaîne de la chaîne de modèle sur lequel la substitution sera effectuée.

*lpsz1*<br/>
Chaîne qui remplace le format de caractères « %1 » dans la chaîne de modèle.

*lpsz2*<br/>
Chaîne qui remplace le format de caractères « %2 » dans la chaîne de modèle.

### <a name="remarks"></a>Notes

La chaîne qui vient d’être formée est stockée dans *rString*. Par exemple, si la chaîne dans la table de chaînes est « Fichier %1 introuvable dans le répertoire %2 », *lpsz1* pointe vers « MYFILE. TXT », et *lpsz2* pointe vers « C:\MYDIR », puis *rString* contient la chaîne « fichier MYFILE. TXT introuvable dans le répertoire C:\MYDIR »

Si le format de caractères « %1 » ou « %2 » apparaître plusieurs fois dans la chaîne, sera plusieurs substitutions. Ils n’ont pas à être dans un ordre numérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

##  <a name="afxmessagebox"></a>  AfxMessageBox

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
Pointe vers un `CString` objet ou une chaîne se terminant par null qui contient le message à afficher dans la boîte de message.

*nType*<br/>
Style de la boîte de message. Appliquer une partie de la [styles de zone de message](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) à la zone.

*nIDHelp*<br/>
L’ID de contexte d’aide pour le message ; 0 indique le que contexte d’aide de l’application par défaut sera utilisé.

*nIDPrompt*<br/>
Un ID unique utilisé pour référencer une chaîne dans la table de chaînes.

### <a name="return-value"></a>Valeur de retour

Zéro en cas de mémoire n’est pas suffisante pour afficher la boîte de message ; Sinon, une des valeurs suivantes est retournée :

- IDABORT le bouton Abandonner a été sélectionné.

- IDCANCEL le bouton Annuler a été sélectionné.

- IDIGNORE le bouton Ignorer a été sélectionné.

- IDNO le bouton non a été sélectionné.

- Bouton de OK le IDOK a été sélectionné.

- IDRETRY le bouton Réessayer a été sélectionné.

- IDYES le bouton Oui a été sélectionné.

Si une boîte de message comporte un bouton Annuler, la valeur IDCANCEL s’affichera si la touche ÉCHAP est enfoncée ou le bouton Annuler est sélectionné. Si la boîte de message n’a aucun bouton Annuler, en appuyant sur la touche ÉCHAP n’a aucun effet.

Les fonctions [AfxFormatString1](#afxformatstring1) et [AfxFormatString2](#afxformatstring2) peut être utile dans la mise en forme de texte qui apparaît dans une boîte de message.

### <a name="remarks"></a>Notes

La première forme de cette fonction surchargée affiche une chaîne de texte vers lequel pointe *lpszText* dans la boîte de message et l’utilise *nIDHelp* pour décrire un contexte d’aide. Le contexte d’aide est utilisé pour accéder à une rubrique d’aide associée lorsque l’utilisateur appuie sur la touche d’aide (généralement F1).

La deuxième forme de la fonction utilise la ressource de chaîne avec l’ID *nIDPrompt* pour afficher un message dans la boîte de message. La page d’aide associée est trouvée à la valeur de *nIDHelp*. Si la valeur par défaut *nIDHelp* est utilisé (-1), l’ID de ressource de chaîne, *nIDPrompt*, est utilisé pour le contexte d’aide. Pour plus d’informations sur la définition des contextes d’aide, consultez [Note technique 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT, classe](../../atl-mfc-shared/reference/cstringt-class.md)
