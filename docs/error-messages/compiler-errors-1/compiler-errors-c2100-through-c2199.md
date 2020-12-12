---
description: 'En savoir plus sur : Erreurs du compilateur C2100 à C2199'
title: Erreurs du compilateur C2100 à C2199
ms.date: 04/21/2019
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
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
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
ms.openlocfilehash: 5948ed2d41a5b20e9c599c6a4c2b27198f8b2d4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318973"
---
# <a name="compiler-errors-c2100-through-c2199"></a>Erreurs du compilateur C2100 à C2199

Les Articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C2100](compiler-error-c2100.md)|indirection non conforme|
|[Erreur du compilateur C2101](compiler-error-c2101.md)|'&' sur constante|
|[Erreur du compilateur C2102](compiler-error-c2102.md)|'&' nécessite une l-value|
|[Erreur du compilateur C2103](compiler-error-c2103.md)|'&' sur variable de registre|
|[Erreur du compilateur C2104](compiler-error-c2104.md)|' & 'sur un champ de bits ignoré|
|[Erreur du compilateur C2105](compiler-error-c2105.md)|'*Operator*'nécessite une l-value|
|[Erreur du compilateur C2106](compiler-error-c2106.md)|'*Operator*' : l’opérande gauche doit être une l-value|
|[Erreur du compilateur C2107](compiler-error-c2107.md)|index non conforme, indirection non autorisée|
|[Erreur du compilateur C2108](compiler-error-c2108.md)|l’indice n’est pas de type intégral|
|[Erreur du compilateur C2109](compiler-error-c2109.md)|l’indice requiert un type tableau ou pointeur|
|[Erreur du compilateur C2110](compiler-error-c2110.md)|' + ' : impossible d’ajouter deux pointeurs|
|[Erreur du compilateur C2111](compiler-error-c2111.md)|' + ' : l’ajout d’un pointeur nécessite un opérande intégral|
|[Erreur du compilateur C2112](compiler-error-c2112.md)|'-' : la soustraction de pointeur requiert un opérande de type intégral ou pointeur|
|[Erreur du compilateur C2113](compiler-error-c2113.md)|'-' : un pointeur ne peut être soustrait que d’un autre pointeur|
|[Erreur du compilateur C2114](compiler-error-c2114.md)|'*Operator*' : pointeur à gauche ; nécessite une valeur intégrale à droite|
|[Erreur du compilateur C2115](compiler-error-c2115.md)|'*opérateur*' : types incompatibles|
|[Erreur du compilateur C2116](compiler-error-c2116.md)|listes de paramètres de fonctions différentes|
|[Erreur du compilateur C2117](compiler-error-c2117.md)|'*identificateur*' : dépassement des limites d’un tableau|
|[Erreur du compilateur C2118](compiler-error-c2118.md)|indice négatif|
|Erreur du compilateur C2119|'*identificateur*' : le type de'*type*'ne peut pas être déduit à partir d’un initialiseur vide|
|[Erreur du compilateur C2120](compiler-error-c2120.md)|'void’non conforme avec tous les types|
|[Erreur du compilateur C2121](compiler-error-c2121.md)|' # ' : caractère non valide : peut-être le résultat d’une expansion macro|
|[Erreur du compilateur C2122](compiler-error-c2122.md)|'*identificateur*' : paramètre de prototype non conforme dans la liste de noms|
|Erreur du compilateur C2123|'*identificateur*' : les modèles d’alias ne peuvent pas être spécialisés explicitement ou partiellement|
|[Erreur du compilateur C2124](compiler-error-c2124.md)|division ou modulo par zéro|
|Erreur du compilateur C2125|'constexpr’est incompatible avec'*Token*'|
|Erreur du compilateur C2126|'*identifier*'ne peut pas être déclaré avec le spécificateur’constexpr'|
|Erreur du compilateur C2127|'*identificateur*' : initialisation non conforme d’une entité’constexpr’avec une expression non constante|
|[Erreur du compilateur C2128](compiler-error-c2128.md)|'*fonction*' : alloc_text/same_seg applicable uniquement aux fonctions avec liaison C|
|[Erreur du compilateur C2129](compiler-error-c2129.md)|fonction statique'*identifier*'déclarée mais non définie|
|[Erreur du compilateur C2130](compiler-error-c2130.md)|#line attendu une chaîne contenant le nom de fichier, '*Token*'trouvé|
|[Erreur du compilateur C2131](compiler-error-c2131.md)|l’expression n’a pas été évaluée en constante|
|[Erreur du compilateur C2132](compiler-error-c2132.md)|erreur de syntaxe : identificateur inattendu|
|[Erreur du compilateur C2133](compiler-error-c2133.md)|'*identificateur*' : taille inconnue|
|[Erreur du compilateur C2134](compiler-error-c2134.md)|'*fonction*' : l’appel ne produit pas une expression constante|
|[Erreur du compilateur C2135](compiler-error-c2135.md)|'*opérateur*' : opération de champ de bits non conforme|
|Erreur du compilateur C2136|contrat d’API de création non autorisé|
|[Erreur du compilateur C2137](compiler-error-c2137.md)|constante caractère vide|
|[Erreur du compilateur C2138](compiler-error-c2138.md)|non conforme pour définir une énumération sans membre|
|[Erreur du compilateur C2139](compiler-error-c2139.md)|'*classe*' : une classe non définie n’est pas autorisée en tant qu’argument pour le trait de type intrinsèque du compilateur'*trait*'|
|[Erreur du compilateur C2140](compiler-error-c2140.md)|'*type*' : un type dépendant d’un paramètre de type générique n’est pas autorisé en tant qu’argument pour le trait de type intrinsèque du compilateur'*trait*'|
|[Erreur du compilateur C2141](compiler-error-c2141.md)|dépassement de la taille du tableau|
|[Erreur du compilateur C2142](compiler-error-c2142.md)|les déclarations de fonction diffèrent, les paramètres de variable spécifiés uniquement dans l’une d’entre elles|
|[Erreur du compilateur C2143](compiler-error-c2143.md)|erreur de syntaxe : '*TOKEN1*'manquant avant'*Token2*'|
|[Erreur du compilateur C2144](compiler-error-c2144.md)|erreur de syntaxe : '*type*'doit être précédé de'*Token2*'|
|[Erreur du compilateur C2145](compiler-error-c2145.md)|erreur de syntaxe : absence de'*Token*'avant l’identificateur|
|[Erreur du compilateur C2146](compiler-error-c2146.md)|erreur de syntaxe : absence de'*Token*'avant l’identificateur'*identifier*'|
|[Erreur du compilateur C2147](compiler-error-c2147.md)|erreur de syntaxe : '*Token*'est un nouveau mot clé|
|[Erreur du compilateur C2148](compiler-error-c2148.md)|la taille totale du tableau ne doit pas dépasser 0x octets de *valeur*|
|[Erreur du compilateur C2149](compiler-error-c2149.md)|'*identificateur*' : un champ de bits nommé ne peut pas avoir une largeur égale à zéro|
|[Erreur du compilateur C2150](compiler-error-c2150.md)|'*identificateur*' : le champ de bits doit être de type’int', 'signed int’ou’unsigned int'|
|[Erreur du compilateur C2151](compiler-error-c2151.md)|plus d’un attribut de langage|
|[Erreur du compilateur C2152](compiler-error-c2152.md)|'*identificateur*' : pointeurs vers des fonctions avec des attributs différents|
|[Erreur du compilateur C2153](compiler-error-c2153.md)|les littéraux entiers doivent comporter au moins un chiffre|
|[Erreur du compilateur C2154](compiler-error-c2154.md)|'*type*' : seul le type énumération est autorisé en tant qu’argument pour le trait de type intrinsèque du compilateur'*trait*'|
|[Erreur du compilateur C2155](compiler-error-c2155.md)|' ? ' : opérande gauche non valide, type arithmétique ou pointeur ATTENDU|
|[Erreur du compilateur C2156](compiler-error-c2156.md)|pragma doit être à l'extérieur de la fonction|
|[Erreur du compilateur C2157](compiler-error-c2157.md)|'*identificateur*' : doit être déclaré avant d’être utilisé dans la liste pragma|
|[Erreur du compilateur C2158](compiler-error-c2158.md)|'*type*' : la directive #pragma make_public est actuellement prise en charge uniquement pour les types non basés sur des modèles natifs|
|[Erreur du compilateur C2159](compiler-error-c2159.md)|plus d'une classe de stockage spécifiée|
|[Erreur du compilateur C2160](compiler-error-c2160.md)|'##' ne peut se trouver au début de la définition d'une macro|
|[Erreur du compilateur C2161](compiler-error-c2161.md)|'##' ne peut se trouver à la fin de la définition d’une macro|
|[Erreur du compilateur C2162](compiler-error-c2162.md)|paramètre formel de macro ATTENDU|
|[Erreur du compilateur C2163](compiler-error-c2163.md)|'*fonction*' : non disponible comme fonction intrinsèque|
|[Erreur du compilateur C2164](compiler-error-c2164.md)|'*fonction*' : fonction intrinsèque non déclarée|
|[Erreur du compilateur C2165](compiler-error-c2165.md)|'*modificateur*' : impossible de modifier les pointeurs vers les données|
|[Erreur du compilateur C2166](compiler-error-c2166.md)|l-value définit un objet const|
|[Erreur du compilateur C2167](compiler-error-c2167.md)|'*fonction*' : paramètres réels de fonction intrinsèque trop nombreux|
|[Erreur du compilateur C2168](compiler-error-c2168.md)|'*fonction*' : nombre de paramètres réels insuffisants pour la fonction intrinsèque|
|[Erreur du compilateur C2169](compiler-error-c2169.md)|'*fonction*' : fonction intrinsèque, ne peut pas être définie|
|[Erreur du compilateur C2170](compiler-error-c2170.md)|'*identifier*' : non déclaré comme fonction, ne peut pas être intrinsèque|
|[Erreur du compilateur C2171](compiler-error-c2171.md)|'*Operator*' : non conforme sur les opérandes de type'*type*'|
|[Erreur du compilateur C2172](compiler-error-c2172.md)|'*fonction*' : le paramètre réel n’est pas un pointeur : paramètre *Number*|
|[Erreur du compilateur C2173](compiler-error-c2173.md)|'*fonction*' : le paramètre réel n’est pas un pointeur : *nombre* de paramètres, *numéro* de la liste de paramètres|
|[Erreur du compilateur C2174](compiler-error-c2174.md)|'*fonction*' : le paramètre réel a le type’void' : le *numéro* de paramètre, le *numéro* de la liste de paramètres|
|[Erreur du compilateur C2175](compiler-error-c2175.md)|'*locale*' : paramètres régionaux non valides|
|Erreur du compilateur C2176|une instruction return ne peut pas apparaître dans le gestionnaire d’un bloc-try de fonction associé à un constructeur|
|[Erreur du compilateur C2177](compiler-error-c2177.md)|constante trop grande|
|[Erreur du compilateur C2178](compiler-error-c2178.md)|'*identifier*'ne peut pas être déclaré avec le spécificateur'*specifier*'|
|[Erreur du compilateur C2179](compiler-error-c2179.md)|'*type*' : un argument d’attribut ne peut pas utiliser de paramètres de type|
|[Erreur du compilateur C2180](compiler-error-c2180.md)|l’expression de contrôle a le type'*type*'|
|[Erreur du compilateur C2181](compiler-error-c2181.md)|instruction else sans if correspondant non conforme|
|[Erreur du compilateur C2182](compiler-error-c2182.md)|'*identificateur*' : utilisation non conforme du type’void'|
|[Erreur du compilateur C2183](compiler-error-c2183.md)|erreur de syntaxe : l’unité de traduction est vide|
|[Erreur du compilateur C2184](compiler-error-c2184.md)|'*type*' : type non conforme pour __except expression|
|[Erreur du compilateur C2185](compiler-error-c2185.md)|'*identificateur*' : allocation de base non conforme|
|[Erreur du compilateur C2186](compiler-error-c2186.md)|'*Operator*' : opérande de type’void’non conforme|
|Erreur du compilateur C2187|erreur de syntaxe : «*Token*» était inattendu ici|
|[Erreur du compilateur C2188](compiler-error-c2188.md)|'*nombre*' : trop grand pour un caractère élargi|
|Erreur du compilateur C2189|l’attribut’alignas’ne peut pas être appliqué à un champ de bits, un paramètre de fonction, une déclaration d’exception ou une variable déclarée avec la classe de stockage’Register'|
|[Erreur du compilateur C2190](compiler-error-c2190.md)|première liste de paramètres plus longue que la seconde|
|[Erreur du compilateur C2191](compiler-error-c2191.md)|seconde liste de paramètres plus longue que la première|
|[Erreur du compilateur C2192](compiler-error-c2192.md)|Déclaration du paramètre'*nombre*'différente|
|[Erreur du compilateur C2193](compiler-error-c2193.md)|'*identificateur*' : déjà dans un segment|
|[Erreur du compilateur C2194](compiler-error-c2194.md)|'*identificateur*' : segment de texte|
|[Erreur du compilateur C2195](compiler-error-c2195.md)|'*identificateur*' : segment de données|
|[Erreur du compilateur C2196](compiler-error-c2196.md)|la valeur case'*value*'est déjà utilisée|
|[Erreur du compilateur C2197](compiler-error-c2197.md)|'*fonction*' : trop d’arguments pour un appel|
|[Erreur du compilateur C2198](compiler-error-c2198.md)|'*fonction*' : nombre d’arguments insuffisant pour l’appel|
|[Erreur du compilateur C2199](compiler-error-c2199.md)|erreur de syntaxe : '*identifier* (') trouvé au niveau de la portée globale (une déclaration était-elle prévue ?)|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
