---
title: Synthèse de la programmation Unicode
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 5095e1c58db3e5c35eb9215367f2fbb064bc228a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504708"
---
# <a name="unicode-programming-summary"></a>Synthèse de la programmation Unicode

Pour tirer parti de la prise en charge de MFC et du runtime C pour Unicode, vous devez :

- Définissez `_UNICODE` .

   Définissez le symbole `_UNICODE` avant de générer votre programme.

- Spécifiez le point d’entrée.

   Dans la page **avancé** du dossier **éditeur de liens** de la boîte de dialogue pages de [Propriétés](../build/reference/property-pages-visual-cpp.md) du projet, définissez le symbole de **point d’entrée** sur `wWinMainCRTStartup` .

- Utilisez des fonctions et des types runtime portables.

   Utilisez les fonctions runtime C appropriées pour la gestion des chaînes Unicode. Vous pouvez utiliser la `wcs` famille de fonctions, mais vous préférerez peut-être préférer les macros entièrement portables (internationalement activé) `_TCHAR` . Ces macros ont toutes le préfixe `_tcs` ; elles remplacent, une par une, pour la `str` famille de fonctions. Ces fonctions sont décrites en détail dans la section [internationalisation](../c-runtime-library/internationalization.md) de la *référence de la bibliothèque Runtime*. Pour plus d’informations, consultez [mappages de texte générique dans Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

   Utilisez `_TCHAR` et les types de données portables associés décrits dans [prise en charge d’Unicode](../text/support-for-unicode.md).

- Gérer correctement les chaînes littérales.

   Le compilateur Visual C++ interprète une chaîne littérale codée comme suit :

    ```cpp
    L"this is a literal string"
    ```

   pour signifier une chaîne de caractères Unicode. Vous pouvez utiliser le même préfixe pour les caractères littéraux. Utilisez la `_T` macro pour coder des chaînes littérales de façon générique, afin qu’elles soient compilées en tant que chaînes Unicode sous Unicode ou en tant que chaînes ANSI (y compris MBCS) sans Unicode. Par exemple, à la place de :

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   faites

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   Avec `_UNICODE` défini, `_T` convertit la chaîne littérale en forme préfixée l ; sinon, `_T` convertit la chaîne sans le préfixe l.

    > [!TIP]
    >  La `_T` macro est identique à la `_TEXT` macro.

- Veillez à passer des longueurs de chaîne aux fonctions.

   Certaines fonctions veulent le nombre de caractères dans une chaîne ; les autres veulent le nombre d’octets. Par exemple, si `_UNICODE` est défini, l’appel suivant à un `CArchive` objet ne fonctionnera pas ( `str` est un `CString` ) :

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   Dans une application Unicode, la longueur vous donne le nombre de caractères, mais pas le nombre correct d’octets, car chaque caractère a une largeur de 2 octets. Au lieu de cela, vous devez utiliser :

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   qui spécifie le nombre correct d’octets à écrire.

   Toutefois, les fonctions membres MFC qui sont orientées caractères plutôt que orientées octets fonctionnent sans ce codage supplémentaire :

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` prend un nombre de caractères, et non un nombre d’octets.

- Utilisez [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) pour ouvrir des fichiers Unicode.

Pour résumer, MFC et la bibliothèque Runtime fournissent la prise en charge suivante pour la programmation Unicode :

- À l’exception des fonctions membres de classe de base de données, toutes les fonctions MFC sont compatibles Unicode, y compris `CString` . `CString` fournit également des fonctions de conversion Unicode/ANSI.

- La bibliothèque Runtime fournit des versions Unicode de toutes les fonctions de gestion de chaînes. (La bibliothèque Runtime fournit également des versions portables appropriées pour Unicode ou pour MBCS. Il s’agit des `_tcs` macros.)

- Tchar. h fournit des types de données portables et la `_T` macro pour traduire des chaînes et des caractères littéraux. Pour plus d’informations, consultez [mappages de texte générique dans Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

- La bibliothèque Runtime fournit une version à caractères larges de `main` . Utilisez `wmain` pour faire en sorte que votre application prenne en charge Unicode.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour Unicode](../text/support-for-unicode.md)
