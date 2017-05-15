---
title: Erreurs du compilateur C2100 through C2199 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
helpviewer_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
dev_langs:
- C++
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: c724fd7907f7ec3f0ce8f096faf88d4ec66ae970
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-errors-c2100-through-c2199"></a>Erreur du compilateurs C2100 through C2199
Les articles de cette partie de la documentation contiennent des informations sur une sous-section des erreurs du compilateur Visual C++. Vous pouvez accéder aux informations ici, ou dans la fenêtre **Sortie** de Visual Studio, vous pouvez sélectionner un numéro d'erreur, puis appuyer sur F1.  
  
> [!NOTE]
>  Pas chaque [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] erreur est documentée dans MSDN. Dans de nombreux cas, le message de diagnostic fournit toutes les informations qui est disponibles. Si vous pensez qu'un message d'erreur nécessite une explication supplémentaire, faites-nous part de vos suggestions. Vous pouvez utiliser le formulaire de commentaires sur cette page, ou accédez à la barre de menus dans Visual Studio et choisissez **aide**, **signaler un bogue**, ou vous pouvez envoyer un rapport de suggestion ou un bogue sur [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Vous trouverez une assistance supplémentaire pour les erreurs et avertissements dans les forums publics MSDN. Le [langage Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) est de forum de questions et de discussions sur les [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxe du langage et du compilateur. Le [Visual C++ général](http://go.microsoft.com/fwlink/?LinkId=158194) est de forum de questions sur [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] qui ne sont pas abordés dans d’autres forums. Vous pouvez également trouver l’aide sur les erreurs et avertissements sur [débordement de pile](http://stackoverflow.com/).  
  
|Erreur|Message|  
|-----------|-------------|  
|[Erreur du compilateur C2100](compiler-error-c2100.md)|indirection non conforme|  
|[Erreur du compilateur C2101](compiler-error-c2101.md)|'&' sur constante|  
|[Erreur du compilateur C2102](compiler-error-c2102.md)|'&' nécessite une l-value|  
|[Erreur du compilateur C2103](compiler-error-c2103.md)|'&' sur variable de registre|  
|[Erreur du compilateur C2104](compiler-error-c2104.md)|' &' sur un champ de bits ignoré|  
|[Erreur du compilateur C2105](compiler-error-c2105.md)|'*opérateur*' nécessite une l-value|  
|[Erreur du compilateur C2106](compiler-error-c2106.md)|'*opérateur*' : opérande gauche doit être l-value|  
|[Erreur du compilateur C2107](compiler-error-c2107.md)|index non conforme, indirection interdite|  
|[Erreur du compilateur C2108](compiler-error-c2108.md)|l'indice n'est pas de type intégral|  
|[Erreur du compilateur C2109](compiler-error-c2109.md)|un indice requiert un type tableau ou pointeur|  
|[Erreur du compilateur C2110](compiler-error-c2110.md)|'+' : Impossible d’ajouter deux pointeurs|  
|[Erreur du compilateur C2111](compiler-error-c2111.md)|'+' : ajout d’un pointeur nécessite un opérande intégral|  
|[Erreur du compilateur C2112](compiler-error-c2112.md)|'-': soustraction de pointeur nécessite un opérande de type intégral ou pointeur|  
|[Erreur du compilateur C2113](compiler-error-c2113.md)|'-': pointeur ne peut être retranché que d’un autre pointeur|  
|[Erreur du compilateur C2114](compiler-error-c2114.md)|'*opérateur*' : pointeur à gauche ; nécessite une valeur intégrale à droite|  
|[Erreur du compilateur C2115](compiler-error-c2115.md)|'*opérateur*' : types incompatibles|  
|[Erreur du compilateur C2116](compiler-error-c2116.md)|listes de paramètres de fonctions différentes|  
|[Erreur du compilateur C2117](compiler-error-c2117.md)|'*identificateur*' : dépassement des limites du tableau|  
|[Erreur du compilateur C2118](compiler-error-c2118.md)|indice négatif|  
|C2119 d’erreur du compilateur|'*identificateur*' : le type de '*type*' ne peut pas être déduit à partir de l’initialiseur vide|  
|[Erreur du compilateur C2120](compiler-error-c2120.md)|'void' non conforme avec tous types|  
|[Erreur du compilateur C2121](compiler-error-c2121.md)|'#' : caractère non valide : peut résulter d'une expansion macro|  
|[Erreur du compilateur C2122](compiler-error-c2122.md)|'*identificateur*' : paramètre de prototype non conforme de liste de nom dans|  
|C2123 d’erreur du compilateur|'*identificateur*' : modèles d’alias ne peut pas être spécialisés explicitement ou partiellement|  
|[Erreur du compilateur C2124](compiler-error-c2124.md)|division ou modulo par zéro|  
|C2125 d’erreur du compilateur|'constexpr' n’est pas compatible avec '*jeton*'|  
|Erreur du compilateur C2126|'*identificateur*' ne peut pas être déclaré avec le spécificateur 'constexpr'|  
|C2127 d’erreur du compilateur|'*identificateur*' : initialisation illégale de l’entité 'constexpr' avec une expression non constante|  
|[Erreur du compilateur C2128](compiler-error-c2128.md)|'*fonction*' : alloc_text/same_seg applicable qu’aux fonctions avec liaison C|  
|[Erreur du compilateur C2129](compiler-error-c2129.md)|fonction static '*identificateur*' déclaré mais ne pas défini|  
|[Erreur du compilateur C2130](compiler-error-c2130.md)|#line attendait une chaîne contenant le nom de fichier, trouvé '*jeton*'|  
|C2131 d’erreur du compilateur|l'expression n'a pas été évaluée en constante|  
|[Erreur du compilateur C2132](compiler-error-c2132.md)|erreur de syntaxe : identificateur inattendu|  
|[Erreur du compilateur C2133](compiler-error-c2133.md)|'*identificateur*' : taille inconnue|  
|[Erreur du compilateur C2134](compiler-error-c2134.md)|'*fonction*' : appel n’entraîne pas une expression constante|  
|[Erreur du compilateur C2135](compiler-error-c2135.md)|'*opérateur*' : opération de champ de bits non conforme|  
|C2136 d’erreur du compilateur|modification de contrat d'API non autorisée|  
|[Erreur du compilateur C2137](compiler-error-c2137.md)|constante caractère vide|  
|[Erreur du compilateur C2138](compiler-error-c2138.md)|il n'est pas conforme de définir une énumération sans membre|  
|[Erreur du compilateur C2139](compiler-error-c2139.md)|'*classe*' : une classe non définie n’est pas autorisée comme argument pour un trait de type intrinsèque du compilateur '*caractéristique*'|  
|[Erreur du compilateur C2140](compiler-error-c2140.md)|'*type*' : un type dépendant d’un paramètre de type générique n’est pas autorisé en tant qu’argument pour un trait de type intrinsèque du compilateur '*caractéristique*'|  
|[Erreur du compilateur C2141](compiler-error-c2141.md)|dépassement de capacité de la taille du tableau|  
|[Erreur du compilateur C2142](compiler-error-c2142.md)|déclarations de fonction différentes, paramètres spécifiés seulement dans l'une d'entre elles|  
|[Erreur du compilateur C2143](compiler-error-c2143.md)|Erreur de syntaxe : manquant '*token1*'before'*token2*'|  
|[Erreur du compilateur C2144](compiler-error-c2144.md)|Erreur de syntaxe : '*type*'doit être précédée par'*token2*'|  
|[Erreur du compilateur C2145](compiler-error-c2145.md)|Erreur de syntaxe : manquant '*jeton*' avant l’identificateur|  
|[Erreur du compilateur C2146](compiler-error-c2146.md)|Erreur de syntaxe : manquant '*jeton*'avant l’identificateur'*identificateur*'|  
|[Erreur du compilateur C2147](compiler-error-c2147.md)|Erreur de syntaxe : '*jeton*' est un nouveau mot clé|  
|[Erreur du compilateur C2148](compiler-error-c2148.md)|taille totale du tableau ne doit pas dépasser 0 x*valeur* octets|  
|[Erreur du compilateur C2149](compiler-error-c2149.md)|'*identificateur*' : un champ de bits nommé ne peut pas avoir de largeur égale à zéro|  
|[Erreur du compilateur C2150](compiler-error-c2150.md)|'*identificateur*' : champ de bits doit être de type 'int', 'signed int' ou 'unsigned int'|  
|[Erreur du compilateur C2151](compiler-error-c2151.md)|plus d'un attribut de langage|  
|[Erreur du compilateur C2152](compiler-error-c2152.md)|'*identificateur*' : pointeurs vers des fonctions avec des attributs différents|  
|[Erreur du compilateur C2153](compiler-error-c2153.md)|les littéraux d'entier doivent comporter au moins un chiffre|  
|[Erreur du compilateur C2154](compiler-error-c2154.md)|'*type*' : seul le type énumération est autorisé en tant qu’argument pour un trait de type intrinsèque du compilateur '*caractéristique*'|  
|[Erreur du compilateur C2155](compiler-error-c2155.md)|'?' : opérande gauche non valide, type arithmétique ou pointeur attendu|  
|[Erreur du compilateur C2156](compiler-error-c2156.md)|pragma doit être à l'extérieur de la fonction|  
|[Erreur du compilateur C2157](compiler-error-c2157.md)|'*identificateur*' : doit être déclaré avant des utiliser dans une liste pragma|  
|[Erreur du compilateur C2158](compiler-error-c2158.md)|'*type*' : la directive #pragma make_public est actuellement prise en charge pour les types sans modèle natifs uniquement|  
|[Erreur du compilateur C2159](compiler-error-c2159.md)|plus d'une classe de stockage spécifiée|  
|[Erreur du compilateur C2160](compiler-error-c2160.md)|'##' ne peut se trouver au début de la définition d'une macro|  
|[Erreur du compilateur C2161](compiler-error-c2161.md)|'##' ne peut se trouver à la fin de la définition d’une macro|  
|[Erreur du compilateur C2162](compiler-error-c2162.md)|paramètre formel de macro attendu|  
|[Erreur du compilateur C2163](compiler-error-c2163.md)|'*fonction*' : non disponible comme fonction intrinsèque|  
|[Erreur du compilateur C2164](compiler-error-c2164.md)|'*fonction*' : fonction intrinsèque non déclarée|  
|[Erreur du compilateur C2165](compiler-error-c2165.md)|'*modificateur*' : ne peut pas modifier les pointeurs sur données|  
|[Erreur du compilateur C2166](compiler-error-c2166.md)|l-value définit un objet const|  
|[Erreur du compilateur C2167](compiler-error-c2167.md)|'*fonction*' : trop de paramètres réels de fonction intrinsèque|  
|[Erreur du compilateur C2168](compiler-error-c2168.md)|'*fonction*' : trop peu de paramètres réels de fonction intrinsèque|  
|[Erreur du compilateur C2169](compiler-error-c2169.md)|'*fonction*' : fonction intrinsèque, ne peut pas être définie.|  
|[Erreur du compilateur C2170](compiler-error-c2170.md)|'*identificateur*' : non déclaré comme fonction, ne peut pas être intrinsèque|  
|[Erreur du compilateur C2171](compiler-error-c2171.md)|'*opérateur*' : non conforme sur les opérandes de type '*type*'|  
|[Erreur du compilateur C2172](compiler-error-c2172.md)|'*fonction*' : le paramètre réel n’est pas un pointeur : paramètre *nombre*|  
|[Erreur du compilateur C2173](compiler-error-c2173.md)|'*fonction*' : le paramètre réel n’est pas un pointeur : paramètre *nombre*, liste de paramètres *nombre*|  
|[Erreur du compilateur C2174](compiler-error-c2174.md)|'*fonction*' : le paramètre réel a 'void 'comme type : paramètre *nombre*, liste de paramètres *nombre*|  
|[Erreur du compilateur C2175](compiler-error-c2175.md)|'*paramètres régionaux*' : variable locale non valide|  
|C2176 d’erreur du compilateur|une instruction return ne peut pas apparaître dans le gestionnaire d'un bloc try de fonction associé à un constructeur|  
|[Erreur du compilateur C2177](compiler-error-c2177.md)|constante trop grande|  
|[C2178 d’erreur du compilateur](compiler-error-c2178.md)|'*identificateur*'ne peut pas être déclarée avec'*spécificateur*' spécificateur|  
|[Erreur du compilateur C2179](compiler-error-c2179.md)|'*type*' : un argument d’attribut ne peut pas utiliser les paramètres de type|  
|[Erreur du compilateur C2180](compiler-error-c2180.md)|expression de contrôle a le type '*type*'|  
|[Erreur du compilateur C2181](compiler-error-c2181.md)|instruction else sans if correspondant non conforme|  
|[Erreur du compilateur C2182](compiler-error-c2182.md)|'*identificateur*' : utilisation non conforme du type 'void'|  
|[Erreur du compilateur C2183](compiler-error-c2183.md)|erreur de syntaxe : unité de traduction vide|  
|[Erreur du compilateur C2184](compiler-error-c2184.md)|'*type*' : type non conforme pour une expression __except|  
|[Erreur du compilateur C2185](compiler-error-c2185.md)|'*identificateur*' : allocation de base non conforme|  
|[Erreur du compilateur C2186](compiler-error-c2186.md)|'*opérateur*' : opérande de type 'void' non conforme|  
|C2187 d’erreur du compilateur|Erreur de syntaxe : '*jeton*' était inattendu ici|  
|[Erreur du compilateur C2188](compiler-error-c2188.md)|'*nombre*' : trop grand pour un caractère large|  
|C2189 d’erreur du compilateur|l’attribut 'alignas' ne peut pas être appliqué à un champ de bits, un paramètre de fonction, une déclaration d’exception ou une variable déclarée avec 'register' classe de stockage|  
|[Erreur du compilateur C2190](compiler-error-c2190.md)|première liste de paramètres plus grande que la seconde|  
|[Erreur du compilateur C2191](compiler-error-c2191.md)|seconde liste de paramètres plus longue que la première|  
|[Erreur du compilateur C2192](compiler-error-c2192.md)|paramètre '*nombre*' déclaration différente|  
|[Erreur du compilateur C2193](compiler-error-c2193.md)|'*identificateur*' : déjà dans un segment|  
|[Erreur du compilateur C2194](compiler-error-c2194.md)|'*identificateur*' : est un segment de texte|  
|[Erreur du compilateur C2195](compiler-error-c2195.md)|'*identificateur*' : est un segment de données|  
|[Erreur du compilateur C2196](compiler-error-c2196.md)|valeur de cas «*valeur*' déjà utilisé|  
|[Erreur du compilateur C2197](compiler-error-c2197.md)|'*fonction*' : trop d’arguments pour l’appel|  
|[Erreur du compilateur C2198](compiler-error-c2198.md)|'*fonction*' : trop peu d’arguments pour l’appel|  
|[Erreur du compilateur C2199](compiler-error-c2199.md)|Erreur de syntaxe : trouvé '*identificateur* (' dans une portée globale (était une déclaration ?)|  
