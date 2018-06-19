---
title: Synthèse de la programmation Unicode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a378d46c517dfc0fbb5857ad54bc31f4c34287b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859675"
---
# <a name="unicode-programming-summary"></a>Synthèse de la programmation Unicode
Pour tirer parti de la prise en charge runtime MFC et C pour Unicode, vous devez :  
  
-   Définir **_UNICODE**.  
  
     Définir le symbole **_UNICODE** avant de générer votre programme.  
  
-   Spécifiez le point d’entrée.  
  
     Sur le **sortie** page du dossier de l’éditeur de liens dans le fichier [Pages de propriétés](../ide/property-pages-visual-cpp.md) boîte de dialogue, définissez le symbole de Point d’entrée **wWinMainCRTStartup**.  
  
-   Utilisez des types et des fonctions runtime portables.  
  
     Utilisez les fonctions d’exécution C correctes pour la gestion des chaînes Unicode. Vous pouvez utiliser la **wcs** famille de fonctions, mais vous pouvez préférer portable entièrement (à l’international activée) **_TCHAR** macros. Ces macros sont toutes le préfixe **_tcs**; ils remplacement, un pour un, pour le **str** famille de fonctions. Ces fonctions sont décrites en détail dans les [internationalisation](../c-runtime-library/internationalization.md) section de la *Run-Time Library Reference*. Pour plus d’informations, consultez [des mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Utilisez **_TCHAR** et les types de données portables associées décrites dans [prise en charge Unicode](../text/support-for-unicode.md).  
  
-   Gérer correctement les chaînes littérales.  
  
     Le compilateur Visual C++ interprète une chaîne littérale codée en tant que :  
  
    ```  
    L"this is a literal string"  
    ```  
  
     pour indiquer une chaîne de caractères Unicode. Vous pouvez utiliser le même préfixe pour les caractères littéraux. Utilisez le **_T** macro pour coder les chaînes littérales génériquement, afin qu’elles soient compilées en tant que chaînes Unicode sous Unicode ou en tant que chaînes ANSI (y compris MBCS) sans Unicode. Par exemple, au lieu de :  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     Utilisation :  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     Avec **_UNICODE** défini, **_T** traduit la chaîne littérale au formulaire avec le préfixe L ; sinon, **_T** traduit la chaîne sans le préfixe L.  
  
    > [!TIP]
    >  Le **_T** macro est identique à la `_TEXT` (macro).  
  
-   Veillez à passer des longueurs de chaîne aux fonctions.  
  
     Certaines fonctions souhaitez que le nombre de caractères dans une chaîne ; d’autres choix le nombre d’octets. Par exemple, si **_UNICODE** est défini, l’appel suivant à un `CArchive` objet ne fonctionne pas (`str` est un `CString`) :  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     Dans une application Unicode, la longueur vous donne le nombre de caractères, mais pas le nombre correct d’octets, car chaque caractère occupe 2 octets. Au lieu de cela, vous devez utiliser :  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     qui spécifie le nombre correct d’octets à écrire.  
  
     Toutefois, les fonctions membres MFC qui sont orientées caractère, plutôt que d’orienté octet, fonctionnent sans codage supplémentaire :  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` prend un nombre de caractères, pas un nombre d’octets.  
  
-   Utilisez [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) pour ouvrir les fichiers Unicode.  
  
 Pour résumer, MFC et la bibliothèque Runtime fournissent la prise en charge suivant pour la programmation Unicode :  
  
-   À l’exception des fonctions membres de classe de base de données, toutes les fonctions MFC sont compatibles Unicode, y compris `CString`. `CString` fournit également des fonctions de conversion Unicode/ANSI.  
  
-   La bibliothèque Runtime fournit les versions Unicode de toutes les fonctions de gestion des chaînes. (La bibliothèque Runtime fournit également des versions portables utilisables pour Unicode ou pour MBCS. Voici le **_tcs** macros.)  
  
-   Tchar.h fournit des types de données portables et **_T** macro pour la traduction des caractères et les chaînes littérales. Pour plus d’informations, consultez [des mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   La bibliothèque Runtime fournit une version à caractères larges de **principal**. Utilisez **wmain** pour rendre votre application prenant en charge Unicode.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge pour Unicode](../text/support-for-unicode.md)