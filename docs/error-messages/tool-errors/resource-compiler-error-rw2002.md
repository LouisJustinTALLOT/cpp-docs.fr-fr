---
title: Erreur RW2002 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 9c5c2824778a679627bd3008276849890f43ac7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190688"
---
# <a name="resource-compiler-error-rw2002"></a>Erreur RW2002 du compilateur de ressources

Erreur d'analyse

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. **Type d’accélérateur requis (ASCII ou VIRTKEY)**

   Le champ `type` de l’instruction **ACCELERATORS** doit contenir la valeur ASCII ou VIRTKEY.

1. **BEGIN attendu dans la table d’accélérateurs**

   Le mot clé **BEGIN** doit suivre immédiatement le mot clé **ACCELERATORS** .

1. **BEGIN attendu dans la boîte de dialogue**

   Le mot clé **Begin** doit suivre immédiatement le mot clé **Dialog** .

1. **BEGIN attendu dans le menu**

   Le mot clé **BEGIN** doit suivre immédiatement le mot clé **MENU** .

1. **BEGIN attendu dans RCData**

   Le mot clé **BEGIN** doit suivre immédiatement le mot clé **RCDATA** .

1. **Mot clé BEGIN attendu dans la table de chaînes**

   Le mot clé **Begin** doit suivre immédiatement le mot clé **STRINGTABLE** .

1. **Impossible de réutiliser les constantes de chaîne**

   Vous utilisez la même valeur deux fois dans une instruction **STRINGTABLE** . Assurez-vous que vous ne mélangez pas les valeurs décimales et hexadécimales qui se chevauchent. Chaque ID dans une **STRINGTABLE** doit être unique. Pour une efficacité maximale, utilisez des constantes contiguës qui démarrent sur un multiple de 16.

1. **Caractère de contrôle hors de la plage [^ A-^ Z]**

   Un caractère de contrôle dans l’instruction **ACCELERATORS** n’est pas valide. Le caractère qui suit le signe insertion ( **^** ) doit être compris entre A et Z, inclusif.

1. **Menus vides non autorisés**

   Un mot clé **end** apparaît avant que tous les éléments de menu ne soient définis dans l’instruction de **menu** . Le compilateur de ressources n’autorise pas les menus vides. Assurez-vous que vous n’avez pas de guillemets ouvrants dans l’instruction de **menu** .

1. **Fin attendue dans la boîte de dialogue**

   Le mot clé **end** doit se trouver à la fin d’une instruction **Dialog** . Assurez-vous qu’il n’y a pas de guillemets ouvrants à gauche de l’instruction précédente.

1. **END attendu dans le menu**

   Le mot clé **END** doit figurer à la fin d’une instruction **MENU** . Assurez-vous que vous n’avez pas des guillemets ouverts ou une paire d’instructions **BEGIN** et **END** sans correspondance.

1. **Virgule attendue dans la table d’accélérateurs**

   Le compilateur de ressources exige une virgule entre les champs `event` et *idvalue* dans l’instruction **ACCELERATORS** .

1. **Nom de classe de contrôle ATTENDU**

   Le champ `class` d’une instruction de **contrôle** dans l’instruction **Dialog** doit être de l’un des types suivants : Button, ComboBox, Edit, ListBox, ScrollBar, static ou défini par l’utilisateur. Assurez-vous que la classe est correctement orthographiée.

1. **Nom de type de police ATTENDU**

   Le champ *typeface* de l’option FONT dans l’instruction **DIALOG** doit être une chaîne de caractères ASCII placée entre guillemets doubles. Ce champ spécifie le nom d’une police.

1. **Valeur d’ID attendue pour MenuItem**

   L’instruction **MENU** doit contenir un champ *menuID* qui spécifie le nom ou le numéro qui identifie la ressource de menu.

1. **Chaîne de menu attendue**

   Chaque instruction **MENUITEM** et **POPUP** doit contenir un champ de *texte* . Ce champ correspond à une chaîne placée entre guillemets doubles qui spécifie le nom de l’élément de menu ou le menu contextuel. Une instruction de **séparateur MenuItem** ne requiert pas de chaîne entre guillemets.

1. **Valeur de commande numérique attendue**

   Le compilateur de ressources attendait un champ *idValue* numérique dans l’instruction **Accelerators** . Assurez-vous que vous avez utilisé une constante `#define` pour spécifier la valeur et que la constante est correctement orthographiée.

1. **Constante numérique attendue dans la table de chaînes**

   Une constante numérique, définie dans une instruction `#define` , doit suivre immédiatement le mot clé **BEGIN** dans une instruction **STRINGTABLE** .

1. **Taille de point numérique attendue**

   Le champ *pointsize* de l’option FONT dans l’instruction **DIALOG** doit être une valeur de taille de point entière.

1. **Constante de boîte de dialogue numérique attendue**

   Une instruction **Dialog** requiert des valeurs entières pour les champs *x, y, Width*et *Height* . Assurez-vous que ces valeurs sont incluses après le mot clé **Dialog** et qu’elles ne sont pas négatives.

1. **Chaîne attendue dans STRINGTABLE**

   Une chaîne est attendue après chaque valeur *stringid* d’une instruction **STRINGTABLE** .

1. **Commande d’accélérateur de constante ou de chaîne attendue**

   Le compilateur de ressources n’a pas pu déterminer quel type de clé est défini pour l’accélérateur. Le champ `event` de l’instruction **ACCELERATORS** peut ne pas être valide.

1. **Nombre attendu pour l’ID**

   Nombre attendu pour le champ `id` d’une instruction de contrôle dans l’instruction **Dialog** . Vérifiez que vous disposez d’une instruction Number ou `#define` pour l’ID de contrôle.

1. **Chaîne entre guillemets attendue dans la classe Dialog**

   Le champ `class` de l’option CLASS figurant dans l’instruction **DIALOG** doit être un entier ou une chaîne, entre guillemets doubles.

1. **Chaîne entre guillemets attendue dans le titre de la boîte de dialogue**

   Le champ `captiontext` de l’option CAPTION figurant dans l’instruction **DIALOG** doit être une chaîne de caractères ASCII placée entre guillemets doubles.

1. **Fichier introuvable : nom de fichier**

   Le fichier spécifié sur la ligne de commande du compilateur de ressources est introuvable. Vérifiez que le fichier a été déplacé vers un autre répertoire et que le nom de fichier ou le chemin est correct. Les fichiers sont recherchés à l’aide de la variable d’environnement **include** ou du paramètre Visual Studio, s’il est disponible.

1. **Les noms de police doivent être des ordinaux**

   Le champ de type de *pointage* de l’instruction font doit être un entier, et non une chaîne.

1. **Accélérateur non valide**

   Un champ `event` de l’instruction **ACCELERATORS** n'a pas été reconnu ou sa longueur dépasse deux caractères.

1. **Type d’accélérateur non valide (ASCII ou VIRTKEY)**

   Le champ `type` de l’instruction **ACCELERATORS** doit contenir la valeur ASCII ou VIRTKEY.

1. **Caractère de contrôle non valide**

   Un caractère de contrôle dans l’instruction **ACCELERATORS** n’est pas valide. Un caractère de contrôle valide se compose d’une lettre (uniquement) après un signe d’insertion (^).

1. **Type de contrôle non valide**

   Chaque instruction de contrôle dans une instruction **Dialog** doit être l’une des suivantes : CheckBox, ComboBox, Control, CTEXT, DEFPUSHBUTTON, EditText, GroupBox, Icon, ListBox, LTEXT, PUSHBUTTON, RadioButton, rtext, ScrollBar. Assurez-vous que ces instructions de contrôle sont correctement orthographiées.

1. **Type non valide**

   Le type de ressource ne faisait pas partie des types définis dans le fichier WINDOWS. h.

1. **Chaîne de texte ou ordinal attendu dans le contrôle**

   Le champ de *texte* d’une instruction de **contrôle** dans l’instruction **Dialog** doit être une chaîne de texte ou une référence ordinale au type de contrôle. S’il s’agit d’un ordinal, veillez à utiliser une instruction `#define` pour le contrôle.

1. **Parenthèses non appariées**

   Vérifiez que vous avez fermé chaque parenthèse ouverte dans l’instruction **Dialog** .

1. **Valeur inattendue dans RCData**

   Les valeurs de *données brutes* de l’instruction **RCDATA** doivent être des entiers ou des chaînes, séparés par une virgule. Assurez-vous de ne pas avoir oublié une virgule ou un guillemet autour d’une chaîne.

1. **Sous-type de menu inconnu**

   Le champ de *définition d’élément* de l’instruction de **menu** peut contenir uniquement des instructions **MenuItem** et **Popup** .
