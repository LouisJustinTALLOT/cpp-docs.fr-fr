---
title: Compilateur erreurs C2000 à C2099
ms.date: 11/17/2017
f1_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
helpviewer_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
ms.assetid: d99a19eb-eeeb-4181-9b33-9cbe4459767b
ms.openlocfilehash: aff0faff5d8e58b46aa6280eb8f259dbd64acee9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548146"
---
# <a name="compiler-errors-c2000-through-c2099"></a>Compilateur erreurs C2000 à C2099

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur qui sont générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|Compilateurs de C2000 Erreur du compilateur|Erreur inconnue choisissez la commande Support technique dans le menu aide de Visual C++ ou ouvrez le fichier d’aide de Support technique pour plus d’informations|
|[Erreur du compilateur C2001](compiler-error-c2001.md)|saut de ligne dans la constante|
|[Erreur du compilateur C2002](compiler-error-c2002.md)|constante à caractères larges non valide|
|[Erreur du compilateur C2003](compiler-error-c2003.md)|attendu 'defined id'|
|[Erreur du compilateur C2004](compiler-error-c2004.md)|attendu 'defined(id)'|
|[Erreur du compilateur C2005](compiler-error-c2005.md)|#line attendait un numéro de ligne, a trouvé '*jeton*'|
|[Erreur du compilateur C2006](compiler-error-c2006.md)|«*directive*' : attendu d’un nom de fichier, trouvé '*jeton*»|
|[Erreur du compilateur C2007](compiler-error-c2007.md)|#define syntaxe|
|[Erreur du compilateur C2008](compiler-error-c2008.md)|«*caractère*' : inattendu dans la définition de macro|
|[Erreur du compilateur C2009](compiler-error-c2009.md)|réutilisation de macro formelle '*identificateur*'|
|[Erreur du compilateur C2010](compiler-error-c2010.md)|«*caractère*' : inattendu dans la liste de paramètres formels de macro|
|[Erreur du compilateur C2011](compiler-error-c2011.md)|«*identificateur*' : '*type*' redéfinition du type|
|[Erreur du compilateur C2012](compiler-error-c2012.md)|nom manquant après '<'|
|[Erreur du compilateur C2013](compiler-error-c2013.md)|'>' manquant|
|[Erreur du compilateur C2014](compiler-error-c2014.md)|commande de préprocesseur doit commencer comme premier espace blanc|
|[Erreur du compilateur C2015](compiler-error-c2015.md)|trop de caractères dans la constante|
|C2016 d’erreur du compilateur|C requiert qu’un struct ou une union possède au moins un membre|
|[Erreur du compilateur C2017](compiler-error-c2017.md)|séquence d’échappement non conforme|
|[Erreur du compilateur C2018](compiler-error-c2018.md)|caractère inconnu ' 0 x*valeur*'|
|[Erreur du compilateur C2019](compiler-error-c2019.md)|directive du préprocesseur attendue, trouvé '*caractère*'|
|[Erreur du compilateur C2020](compiler-error-c2020.md)|«*membre*' : '*classe*' redéfinition du membre|
|[Erreur du compilateur C2021](compiler-error-c2021.md)|pas de valeur d’exposant, d’attendue '*caractère*'|
|[Erreur du compilateur C2022](compiler-error-c2022.md)|«*nombre*' : trop grand pour un caractère|
|C2023 d’erreur du compilateur|«*identificateur*' : alignement (*number1*) diffère de la déclaration antérieure (*number2*)|
|C2024 d’erreur du compilateur|l’attribut 'alignas' s’applique aux variables, les membres de données et les types de balises uniquement|
|C2025 d’erreur du compilateur|fichier d’interface de module binaire non valide ou endommagé : '*filename*'|
|[Erreur du compilateur C2026](compiler-error-c2026.md)|chaîne trop grande, caractères de fin tronqués|
|[Erreur du compilateur C2027](compiler-error-c2027.md)|utilisation du type non défini '*type*'|
|[Erreur du compilateur C2028](compiler-error-c2028.md)|un membre struct/union doit être dans un struct/union|
|C2029 d’erreur du compilateur|gauche de '*jeton*'spécifie la classe/struct/interface non défini'*identificateur*'|
|[Erreur du compilateur C2030](compiler-error-c2030.md)|un destructeur avec l'accessibilité 'protected private' ne peut pas être membre d'une classe déclarée 'sealed'|
|C2031 d’erreur du compilateur|un destructeur virtuel avec '*accessibilité*' accessibilité n’est pas autorisée pour ce type|
|[Erreur du compilateur C2032](compiler-error-c2032.md)|«*identificateur*' : fonction ne peut pas être membre de struct/union '*type*»|
|[Erreur du compilateur C2033](compiler-error-c2033.md)|«*identificateur*' : un champ de bits ne peut pas avoir d’indirection|
|[Erreur du compilateur C2034](compiler-error-c2034.md)|«*identificateur*' : type de champ de bits trop petit pour le nombre de bits|
|C2035 d’erreur du compilateur|un destructeur non virtuel avec '*accessibilité*' accessibilité n’est pas autorisée pour ce type|
|[Erreur du compilateur C2036](compiler-error-c2036.md)|«*identificateur*' : taille inconnue|
|C2037 d’erreur du compilateur|gauche de '*identificateur*'Spécifie un struct/union non défini'*type*'|
|C2038 d’erreur du compilateur|l’espace de noms std ne peut pas être inline|
|[Erreur du compilateur C2039](compiler-error-c2039.md)|«*identificateur1*' : n’est pas un membre de '*identificateur2*»|
|[Erreur du compilateur C2040](compiler-error-c2040.md)|«*opérateur*' : '*identificateur1*'diffère dans les niveaux d’indirection de'*identificateur2*»|
|[Erreur du compilateur C2041](compiler-error-c2041.md)|chiffre non conforme '*caractère*'pour la base de'*nombre*'|
|[Erreur du compilateur C2042](compiler-error-c2042.md)|les mots clés signed/unsigned s'excluent mutuellement|
|[Erreur du compilateur C2043](compiler-error-c2043.md)|instruction break non conforme|
|[Erreur du compilateur C2044](compiler-error-c2044.md)|instruction continue non conforme|
|[Erreur du compilateur C2045](compiler-error-c2045.md)|«*identificateur*' : étiquette redéfinie|
|[Erreur du compilateur C2046](compiler-error-c2046.md)|instruction case non conforme|
|[Erreur du compilateur C2047](compiler-error-c2047.md)|instruction default non conforme|
|[Erreur du compilateur C2048](compiler-error-c2048.md)|plusieurs 'default'|
|C2049 d’erreur du compilateur|«*identificateur*' : espace de noms non inline ne peut pas être rouverte comme inline|
|[Erreur du compilateur C2050](compiler-error-c2050.md)|expression de switch non intégrale|
|[Erreur du compilateur C2051](compiler-error-c2051.md)|expression case est pas une constante|
|[Erreur du compilateur C2052](compiler-error-c2052.md)|«*type*' : type non conforme pour une expression case|
|[Erreur du compilateur C2053](compiler-error-c2053.md)|«*identificateur*' : incompatibilité de chaînes étendues|
|[Erreur du compilateur C2054](compiler-error-c2054.md)|attendu ' (' suivre '*identificateur*'|
|[Erreur du compilateur C2055](compiler-error-c2055.md)|liste de paramètres formels attendue, non une liste de type|
|[Erreur du compilateur C2056](compiler-error-c2056.md)|expression non conforme|
|[Erreur du compilateur C2057](compiler-error-c2057.md)|expression constante attendue|
|[Erreur du compilateur C2058](compiler-error-c2058.md)|expression constante non intégrale|
|[Erreur du compilateur C2059](compiler-error-c2059.md)|Erreur de syntaxe : '*jeton*'|
|[Erreur du compilateur C2060](compiler-error-c2060.md)|Erreur de syntaxe : fin de fichier|
|[Erreur du compilateur C2061](compiler-error-c2061.md)|Erreur de syntaxe : identificateur '*identificateur*'|
|[Erreur du compilateur C2062](compiler-error-c2062.md)|type '*type*' inattendu|
|[Erreur du compilateur C2063](compiler-error-c2063.md)|«*identificateur*' : pas d’une fonction|
|[Erreur du compilateur C2064](compiler-error-c2064.md)|le terme ne correspond pas à une prise de fonction *nombre* arguments|
|[Erreur du compilateur C2065](compiler-error-c2065.md)|«*identificateur*' : identificateur non déclaré|
|[Erreur du compilateur C2066](compiler-error-c2066.md)|cast en type fonction n’est pas conforme|
|[Erreur du compilateur C2067](compiler-error-c2067.md)|cast en type tableau non conforme|
|C2068 d’erreur du compilateur|utilisation non conforme d’une fonction surchargée. Liste d’arguments manquante ?|
|[Erreur du compilateur C2069](compiler-error-c2069.md)|cast d'un terme 'void' en non 'void'|
|[Erreur du compilateur C2070](compiler-error-c2070.md)|«*type*' : opérande sizeof non conforme|
|[Erreur du compilateur C2071](compiler-error-c2071.md)|«*identificateur*' : classe de stockage non conforme|
|[Erreur du compilateur C2072](compiler-error-c2072.md)|«*identificateur*' : l’initialisation d’une fonction|
|[Erreur du compilateur C2073](compiler-error-c2073.md)|«*identificateur*' : les éléments d’un tableau partiellement initialisé doivent avoir un constructeur par défaut|
|[Erreur du compilateur C2074](compiler-error-c2074.md)|«*identificateur*' : '*type*' initialisation nécessite une liste d’initialiseurs entre accolades|
|[Erreur du compilateur C2075](compiler-error-c2075.md)|«*identificateur*' : l’initialisation de tableau nécessite une liste d’initialiseurs entre accolades|
|C2076 d’erreur du compilateur|une liste d’initialiseurs entre accolades ne peut pas être utilisée dans une expression new dont le type contient '*type*'|
|[Erreur du compilateur C2077](compiler-error-c2077.md)|initialiseur de champ non scalaire '*identificateur*'|
|[Erreur du compilateur C2078](compiler-error-c2078.md)|initialiseurs trop nombreux|
|[Erreur du compilateur C2079](compiler-error-c2079.md)|«*identificateur*'utilise undefined class/struct/union'*type*»|
|C2080 d’erreur du compilateur|«*identificateur*' : le type de '*type*' ne peut être déduit qu’à partir d’une seule expression d’initialiseur|
|[Erreur du compilateur C2081](compiler-error-c2081.md)|«*identificateur*' : nom non conforme de liste de paramètres formels dans|
|[Erreur du compilateur C2082](compiler-error-c2082.md)|redéfinition du paramètre formel '*identificateur*'|
|[Erreur du compilateur C2083](compiler-error-c2083.md)|comparaison struct/union non conforme|
|[Erreur du compilateur C2084](compiler-error-c2084.md)|fonction '*identificateur*' a déjà un corps|
|[Erreur du compilateur C2085](compiler-error-c2085.md)|«*identificateur*' : pas dans la liste de paramètres formels|
|[Erreur du compilateur C2086](compiler-error-c2086.md)|«*identificateur*' : redéfinition|
|[Erreur du compilateur C2087](compiler-error-c2087.md)|«*identificateur*' : indice manquant|
|[Erreur du compilateur C2088](compiler-error-c2088.md)|«*opérateur*' : non conforme pour la classe/struct/union|
|[Erreur du compilateur C2089](compiler-error-c2089.md)|«*identificateur*' : '*type*' trop grande|
|[Erreur du compilateur C2090](compiler-error-c2090.md)|Retourne un tableau (fonction)|
|[Erreur du compilateur C2091](compiler-error-c2091.md)|fonction retourne (fonction)|
|[Erreur du compilateur C2092](compiler-error-c2092.md)|«*identificateur*' type d’élément de tableau ne peut pas être (fonction)|
|[Erreur du compilateur C2093](compiler-error-c2093.md)|«*identificateur1*' : ne peut pas être initialisée à l’aide de l’adresse de la variable automatique '*identificateur2*»|
|[Erreur du compilateur C2094](compiler-error-c2094.md)|étiquette '*identificateur*' n’était pas défini|
|[Erreur du compilateur C2095](compiler-error-c2095.md)|«*fonction*' : le paramètre réel a le type 'void' : paramètre *nombre*|
|C2096 d’erreur du compilateur|«*identificateur*' : un membre de données ne peut pas être initialisé avec un initialiseur entre parenthèses|
|[Erreur du compilateur C2097](compiler-error-c2097.md)|initialisation non conforme|
|C2098 d’erreur du compilateur|jeton inattendu après le membre de données '*identificateur*'|
|[Erreur du compilateur C2099](compiler-error-c2099.md)|l'initialiseur n'est pas une constante|
