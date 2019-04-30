---
title: Synthèse de la programmation Unicode
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 130c9027a882de2aae7fb339e4761b0cc81b3a6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410510"
---
# <a name="unicode-programming-summary"></a>Synthèse de la programmation Unicode

Pour tirer parti de la prise en charge runtime C et MFC pour Unicode, vous devez :

- Définir `_UNICODE`.

   Définissez le symbole `_UNICODE` avant de générer votre programme.

- Spécifier le point d’entrée.

   Sur le **avancé** page de la **l’éditeur de liens** dossier dans le projet [Pages de propriétés](../ide/property-pages-visual-cpp.md) boîte de dialogue, définissez la **Point d’entrée** symbole à `wWinMainCRTStartup`.

- Utiliser des types et des fonctions runtime portables.

   Utilisez les fonctions d’exécution C correctes pour la gestion des chaînes Unicode. Vous pouvez utiliser la `wcs` famille de fonctions, mais vous préférerez peut-être portable entièrement (est-elle activée) `_TCHAR` macros. Ces macros sont toutes le préfixe `_tcs`; ils remplacement, une pour l’une, pour le `str` famille de fonctions. Ces fonctions sont décrites en détail dans le [internationalisation](../c-runtime-library/internationalization.md) section de la *Run-Time Library Reference*. Pour plus d’informations, consultez [des mappages de texte générique dans tchar.h](../text/generic-text-mappings-in-tchar-h.md).

   Utilisez `_TCHAR` et les types de données portables associées décrites dans [prise en charge Unicode](../text/support-for-unicode.md).

- Gérer correctement les chaînes littérales.

   Le compilateur Visual C++ interprète une chaîne littérale codée en tant que :

    ```cpp
    L"this is a literal string"
    ```

   pour indiquer une chaîne de caractères Unicode. Vous pouvez utiliser le même préfixe pour les caractères littéraux. Utilisez le `_T` macro pour coder les chaînes littérales génériquement, afin qu’elles soient compilées en tant que chaînes Unicode sous Unicode ou en tant que chaînes ANSI (y compris MBCS) sans Unicode. Par exemple, au lieu de :

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   Utilisation :

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   Avec `_UNICODE` défini, `_T` traduit la chaîne littérale pour le formulaire avec le préfixe L ; sinon, `_T` traduit la chaîne sans le préfixe L.

    > [!TIP]
    >  Le `_T` macro est identique à la `_TEXT` (macro).

- Soyez prudent en passant des longueurs de chaîne aux fonctions.

   Certaines fonctions obtenir le nombre de caractères dans une chaîne ; d’autres veulent le nombre d’octets. Par exemple, si `_UNICODE` est défini, l’appel suivant à un `CArchive` objet ne fonctionne pas (`str` est un `CString`) :

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   Dans une application Unicode, la longueur vous donne le nombre de caractères, mais pas le nombre correct d’octets, car chaque caractère est égale à 2 octets. Au lieu de cela, vous devez utiliser :

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   qui spécifie le nombre correct d’octets à écrire.

   Toutefois, les fonctions membres MFC qui sont orientées caractère, plutôt que d’orienté octet, fonctionnent sans codage supplémentaire :

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` prend un nombre de caractères, pas un nombre d’octets.

- Utilisez [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) pour ouvrir les fichiers Unicode.

Pour résumer, MFC et la bibliothèque Runtime fournissent la prise en charge suivante pour la programmation Unicode :

- À l’exception des fonctions de membre de classe de base de données, toutes les fonctions MFC sont compatibles Unicode, y compris `CString`. `CString` fournit également des fonctions de conversion Unicode/ANSI.

- La bibliothèque Runtime fournit les versions Unicode de toutes les fonctions de gestion des chaînes. (La bibliothèque Runtime fournit également des versions portables utilisables pour Unicode ou pour MBCS. Il s’agit de la `_tcs` macros.)

- Tchar.h fournit des types de données portables et `_T` macro pour la traduction des caractères et des chaînes littérales. Pour plus d’informations, consultez [des mappages de texte générique dans tchar.h](../text/generic-text-mappings-in-tchar-h.md).

- La bibliothèque d’exécution fournit une version à caractères larges de `main`. Utilisez `wmain` pour rendre votre application prenant en charge Unicode.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour Unicode](../text/support-for-unicode.md)
