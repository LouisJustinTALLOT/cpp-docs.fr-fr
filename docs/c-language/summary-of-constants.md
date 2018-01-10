---
title: "Récapitulatif des constantes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e46966d56084a615ffdf2763adefbcd1e416a6ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-constants"></a>Récapitulatif des constantes
`constant`:  
 *floating-point-constant*  
  
 *integer-constant*  
  
 *enumeration-constant*  
  
 *character-constant*  
  
 *floating-point-constant* :  
 *fractional-constant exponent-part* opt*floating-suffix* opt  
  
 *digit-sequence exponent-part floating-suffix* opt  
  
 *fractional-constant* :  
 *digit-sequence* opt**.***digit-sequence*  
  
 *digit-sequence*  **.**  
  
 *exponent-part* :  
 **e**  *sign* opt*digit-sequence*  
  
 **E**  *sign* opt*digit-sequence*  
  
 *sign* : un des éléments suivants  
 **+ -**  
  
 *digit-sequence* :  
 *digit*  
  
 *digit-sequence digit*  
  
 *floating-suffix* : un des éléments suivants  
 **f l F L**  
  
 *integer-constant* :  
 *decimal-constant integer-suffix* opt  
  
 *octal-constant integer-suffix* opt  
  
 *hexadecimal-constant integer-suffix* opt  
  
 *decimal-constant*:  
 *nonzero-digit*  
  
 *decimal-constant digit*  
  
 *octal-constant* :  
 **0**  
  
 *octal-constant octal-digit*  
  
 *hexadecimal-constant* :  
 **0x**  *hexadecimal-digit*  
  
 **0X**  *hexadecimal-digit*  
  
 *hexadecimal-constant hexadecimal-digit*  
  
 *nonzero-digit* : un des éléments suivants :  
 **1 2 3 4 5 6 7 8 9**  
  
 *octal-digit* : un des éléments suivants :  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimal-digit* : un des éléments suivants :  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **a b c d e f**  
  
 **A B C D E F**  
  
 *unsigned-suffix* : un des éléments suivants :  
 **u U**  
  
 *long-suffix* : un des éléments suivants :  
 **l L**  
  
 *character-constant* :  
 **'** *c-char-sequence*  
  
 **'L'** *c-char-sequence* **'**  
  
 *integer-suffix* :  
 *unsigned-suffix long-suffix* opt  
  
 *long-suffix unsigned-suffix* opt  
  
 *c-char-sequence* :  
 *c-char*  
  
 *c-char-sequence c-char*  
  
 *c-char* :  
 Tout membre du jeu de caractères de code source, sauf le guillemet simple ('), la barre oblique inverse (**\\**) ou la *séquence d’échappement* de caractère de saut de ligne  
  
 *escape-sequence* :  
 *simple-escape-sequence*  
  
 *octal-escape-sequence*  
  
 *hexadecimal-escape-sequence*  
  
 *simple-escape-sequence* : un des éléments suivants :  
 **\a \b \f \n \r \t \v**  
  
 **\\' \\" \\\ \\?**  
  
 *octal-escape-sequence* :  
 **\\** *octal-digit*  
  
 **\\** *octal-digit octal-digit*  
  
 **\\** *octal-digit octal-digit octal-digit*  
  
 *hexadecimal-escape-sequence* :  
 **\x**  *hexadecimal-digit*  
  
 *hexadecimal-escape-sequence hexadecimal-digit*  
  
## <a name="see-also"></a>Voir aussi  
 [Grammaire lexicale](../c-language/lexical-grammar.md)