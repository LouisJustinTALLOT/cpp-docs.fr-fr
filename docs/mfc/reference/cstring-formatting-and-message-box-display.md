---
description: 'En savoir plus sur les éléments suivants : mise en forme de CString et affichage des Message-Box'
title: Mise en forme de CString et affichage des boîtes de message
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: a3c91a2a8a6f80235a834811433467797d5a37a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264516"
---
# <a name="cstring-formatting-and-message-box-display"></a>Mise en forme de CString et affichage des boîtes de message

Plusieurs fonctions sont fournies pour mettre en forme et analyser les `CString` objets. Vous pouvez utiliser ces fonctions chaque fois que vous devez manipuler `CString` des objets, mais elles sont particulièrement utiles pour mettre en forme les chaînes qui s’affichent dans le texte de la boîte de message.

Ce groupe de fonctions comprend également une routine globale pour l’affichage d’une boîte de message.

### <a name="cstring-functions"></a>Fonctions CString

|Nom|Description|
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrait des sous-chaînes séparées par un caractère unique à partir d’une chaîne source donnée.|
|[AfxFormatString1](#afxformatstring1)|Remplace une chaîne donnée pour les caractères de format « %1 » dans une chaîne contenue dans la table de chaînes.|
|[AfxFormatString2](#afxformatstring2)|Remplace deux chaînes pour les caractères de format "%1" et "%2" dans une chaîne contenue dans la table de chaînes.|
|[AfxMessageBox](#afxmessagebox)|Affiche une boîte de message.|

### <a name="requirements"></a>Spécifications

  **En-tête** AFXWIN. h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a> AfxExtractSubString

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
Référence à un objet [CString](../../atl-mfc-shared/using-cstring.md) qui recevra une sous-chaîne individuelle.

*lpszFullString*<br/>
Chaîne contenant le texte complet de la chaîne à extraire.

*iSubString*<br/>
Index de base zéro de la sous-chaîne à extraire de *lpszFullString*.

*chSep*<br/>
Caractère de séparation utilisé pour délimiter des sous-chaînes.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fonction a extrait avec succès la sous-chaîne à l’index fourni ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette fonction est utile pour extraire plusieurs sous-chaînes d’une chaîne source lorsqu’un caractère unique connu sépare chaque sous-chaîne. Cette fonction recherche à partir du début du paramètre *lpszFullString* chaque fois qu’elle est appelée.

Cette fonction retourne FALSe si *lpszFullString* a la valeur null ou si la fonction atteint la fin de *LpszFullString* sans rechercher *iSubString*+ 1 occurrences du caractère de séparation spécifié. Le paramètre *rString* ne sera pas modifié à partir de sa valeur d’origine si *lpszFullString* était défini sur null ; dans le cas contraire, le paramètre *rString* est défini sur la chaîne vide si la sous-chaîne n’a pas pu être extraite pour l’index spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** AFXWIN. h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a> AfxFormatString1

Remplace la chaîne pointée par *lpsz1* pour toutes les instances des caractères « %1 » dans la ressource de chaîne de modèle identifiée par *nIDS*.

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Référence à un `CString` objet qui contiendra la chaîne résultante après l’exécution de la substitution.

*nIDS*<br/>
ID de ressource de la chaîne de modèle sur laquelle la substitution sera effectuée.

*lpsz1*<br/>
Chaîne qui remplacera les caractères de format « %1 » dans la chaîne du modèle.

### <a name="remarks"></a>Notes

La chaîne nouvellement formée est stockée dans *rString*. Par exemple, si la chaîne de la table de chaînes est « fichier %1 introuvable » et que *lpsz1* est égal à « C:\MYFILE.TXT », *rString* contient la chaîne « fichier C:\MYFILE.TXT introuvable ». Cette fonction est utile pour mettre en forme des chaînes envoyées à des boîtes de message et à d’autres fenêtres.

Si les caractères de format « %1 » apparaissent plusieurs fois dans la chaîne, plusieurs substitutions sont effectuées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** AFXWIN. h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a> AfxFormatString2

Remplace la chaîne pointée par *lpsz1* pour toutes les instances des caractères « %1 », et la chaîne pointée par *lpsz2* pour toutes les instances des caractères « %2 », dans la ressource de modèle de chaîne identifiée par *nIDS*.

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Référence à `CString` qui contiendra la chaîne résultante après l’exécution de la substitution.

*nIDS*<br/>
ID de la table de chaînes de la chaîne de modèle sur laquelle la substitution sera effectuée.

*lpsz1*<br/>
Chaîne qui remplacera les caractères de format « %1 » dans la chaîne du modèle.

*lpsz2*<br/>
Chaîne qui remplacera les caractères de format « %2 » dans la chaîne du modèle.

### <a name="remarks"></a>Notes

La chaîne nouvellement formée est stockée dans *rString*. Par exemple, si la chaîne de la table de chaînes est « le fichier %1 est introuvable dans le répertoire %2 », *lpsz1* pointe vers « MYFILE.TXT » et *lpsz2* pointe vers « C:\MYDIR », puis *RString* contient la chaîne « fichier MYFILE.TXT introuvable dans le répertoire C:\MYDIR »

Si les caractères de format "%1" ou "%2" apparaissent plusieurs fois dans la chaîne, plusieurs substitutions sont effectuées. Ils n’ont pas besoin d’être dans l’ordre numérique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** AFXWIN. h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a> AfxMessageBox

Affiche une boîte de message à l’écran.

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
Pointe vers un `CString` objet ou une chaîne se terminant par un caractère null qui contient le message à afficher dans la boîte de message.

*nType*<br/>
Style de la boîte de message. Appliquez l’un des [styles de boîte de message](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) à la zone.

*nIDHelp*<br/>
ID de contexte d’aide pour le message ; 0 indique que le contexte d’aide par défaut de l’application sera utilisé.

*nIDPrompt*<br/>
ID unique utilisé pour référencer une chaîne dans la table de chaînes.

### <a name="return-value"></a>Valeur renvoyée

Zéro s’il n’y a pas assez de mémoire pour afficher la boîte de message ; Sinon, l’une des valeurs suivantes est retournée :

- IDABORT le bouton abandonner a été sélectionné.

- IDCANCEL le bouton Annuler a été sélectionné.

- IDIGNORE le bouton ignorer a été sélectionné.

- IDNO le bouton non a été sélectionné.

- IDOK le bouton OK a été sélectionné.

- IDRETRY le bouton Réessayer a été sélectionné.

- IDYES le bouton Oui a été sélectionné.

Si une boîte de message contient un bouton Annuler, la valeur IDCANCEL est retournée si la touche Échap est enfoncée ou si le bouton Annuler est sélectionné. Si la boîte de message n’a pas de bouton Annuler, le fait d’appuyer sur la touche Échap n’a aucun effet.

Les fonctions [AfxFormatString1](#afxformatstring1) et [AfxFormatString2](#afxformatstring2) peuvent être utiles pour mettre en forme le texte qui s’affiche dans une boîte de message.

### <a name="remarks"></a>Notes

La première forme de cette fonction surchargée affiche une chaîne de texte pointée par *lpszText* dans la boîte de message et utilise *nIDHelp* pour décrire un contexte d’aide. Le contexte d’aide est utilisé pour accéder à une rubrique d’aide associée lorsque l’utilisateur appuie sur la touche d’aide (en général, la touche F1).

La deuxième forme de la fonction utilise la ressource de type chaîne avec l’ID *nIDPrompt* pour afficher un message dans la boîte de message. La page d’aide associée est trouvée via la valeur de *nIDHelp*. Si la valeur par défaut de *nIDHelp* est utilisée (-1), l’ID de ressource de chaîne, *nIDPrompt*, est utilisé pour le contexte d’aide. Pour plus d’informations sur la définition de contextes d’aide, consultez [Technical Note 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT (classe)](../../atl-mfc-shared/reference/cstringt-class.md)
