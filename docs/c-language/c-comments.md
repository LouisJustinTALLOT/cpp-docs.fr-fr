---
title: Commentaires en C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 78c3e97530198b6685e402237bda5cdaf9a0754a
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="c-comments"></a>Commentaires en C
Un « commentaire » est une séquence de caractères commençant par la combinaison d’une barre oblique et d’un astérisque (<b>/\*</b>), traitée comme un espace blanc par le compilateur ou ignoré. Un commentaire peut inclure toute combinaison de caractères du jeu de caractères utilisable, y compris les caractères de saut de ligne, à l’exclusion du séparateur « de fin de commentaire » (<b>\*/</b>). Les commentaires peuvent occuper plusieurs lignes mais ne peuvent pas être imbriqués.  
  
 Ils peuvent être placés partout où un espace blanc est autorisé. Comme le compilateur traite un commentaire en tant qu'espace blanc unique, vous ne pouvez pas inclure de commentaires dans des jetons. Le compilateur ignore les caractères figurant dans un commentaire.  
  
 Utilisez les commentaires pour documenter votre code. L'exemple suivant est un commentaire accepté par le compilateur :  
  
```  
/* Comments can contain keywords such as  
   for and while without generating errors. */  
```  
  
 Des commentaires peuvent figurer sur la même ligne qu'une instruction de code :  
  
```  
printf( "Hello\n" );  /* Comments can go here */  
```  
  
 Vous pouvez décider de placer un bloc de commentaires descriptifs avant des fonctions ou des modules de programme :  
  
```  
/* MATHERR.C illustrates writing an error routine   
 * for math functions.   
 */   
```  
  
 Comme les commentaires ne peuvent pas contenir de commentaires imbriqués, l'exemple suivant génère une erreur :  
  
```  
/* Comment out this routine for testing   
  
   /* Open file */  
    fh = _open( "myfile.c", _O_RDONLY );  
    .  
    .  
    .  
 */  
```  
  
 L'erreur survient parce que le compilateur identifie la première combinaison `*/`, après les mots `Open file`, comme la fin du commentaire. Il essaie de traiter la suite du texte et génère une erreur lorsqu'il trouve la combinaison `*/` en dehors d'un commentaire.  
  
 Bien que vous puissiez utiliser des commentaires pour rendre inactives certaines lignes de code à des fins de test, les directives de préprocesseur `#if` et `#endif`, ainsi que la compilation conditionnelle, représentent une alternative utile pour cette tâche. Pour plus d’informations, consultez [Directives de préprocesseur](../preprocessor/preprocessor-directives.md) dans *Informations de référence sur le préprocesseur*.  
  
 **Section spécifique à Microsoft**  
  
 Le compilateur Microsoft prend également en charge les commentaires d’une seule ligne précédés de deux barres obliques (**//**). Lors d'une compilation avec /Za (norme ANSI), ces commentaires génèrent des erreurs. De tels commentaires ne peuvent pas être étendus à une deuxième ligne.  
  
```  
// This is a valid comment  
```  
  
 Les commentaires commençant par deux barres obliques (**//**) se terminent par le caractère de saut de ligne suivant qui n’est pas précédé d’un caractère d’échappement. Dans l’exemple suivant, le caractère de saut de ligne est précédé d’une barre oblique inverse (**\\**), créant ainsi une « séquence d’échappement ». Cette séquence d'échappement indique au compilateur de traiter la ligne suivante dans le cadre de la ligne précédente. (Pour plus d’informations, consultez [Séquences d’échappement](../c-language/escape-sequences.md).)  
  
```  
// my comment \  
    i++;   
```  
  
 Par conséquent, l'instruction `i++;` est mise en commentaires.  
  
 Par défaut pour Microsoft C, les extensions Microsoft sont activées. Utilisez /Za pour désactiver ces extensions.  
  
 **Fin de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Jetons C](../c-language/c-tokens.md)

