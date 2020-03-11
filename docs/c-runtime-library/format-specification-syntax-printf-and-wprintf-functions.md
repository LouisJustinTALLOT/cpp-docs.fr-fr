---
title: 'Syntaxe de spécification de format : fonctions printf et wprintf'
ms.date: 10/21/2019
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
ms.openlocfilehash: 024e757f57e62ba2b30048c783798180b4da2b9a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865490"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntaxe de spécification de format : fonctions printf et wprintf

Les différentes fonctions `printf` et `wprintf` acceptent une chaîne de format et des arguments facultatifs, et génèrent en sortie une séquence de caractères mise en forme. La chaîne de format contient zéro ou plusieurs *directives* qui sont soit des caractères littéraux pour la sortie, soit des *spécifications de conversion* codées qui décrivent comment mettre en forme un argument dans la sortie. Cet article décrit la syntaxe utilisée pour encoder les spécifications de conversion dans la chaîne de format. Pour obtenir la liste de ces fonctions, consultez [E/S de flux](../c-runtime-library/stream-i-o.md). 

Une spécification de conversion se compose de champs facultatifs et obligatoires mis en forme comme suit :

**%** [[*flags*](#flags)][[*width*](#width)][.[*precision*](#precision)][[*size*](#size)][*type*](#type)

Chaque champ de la spécification de conversion est un caractère ou un nombre qui représente un spécificateur d’option ou de conversion de format particulier. Le champ obligatoire *type* spécifie le genre de conversion à appliquer à un argument. Les champs facultatifs *flags*, *width* et *precision* contrôlent d’autres aspects du format, notamment les espaces ou les zéros de début, la justification et la précision affichée. Le champ *size* spécifie la taille de l’argument consommé et converti.

Une spécification de conversion de base contient uniquement le symbole de pourcentage et un caractère *type*. Par exemple, `%s` spécifie une conversion de chaîne. Pour imprimer un caractère de pourcentage, utilisez `%%`. Si un signe de pourcentage est suivi d’un caractère qui n’a aucune signification en tant que champ de format, le gestionnaire de paramètres non valides est appelé. Pour plus d’informations, consultez [Validation de paramètre](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Pour garantir la sécurité et la stabilité, vérifiez que ces chaînes de spécification de conversion ne sont pas définies par l’utilisateur. Par exemple, imaginez un programme qui invite l'utilisateur à entrer un nom et enregistre l'entrée dans une variable de chaîne nommée `user_name`. Pour imprimer `user_name`, n'effectuez pas l'opération suivante :
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Procédez plutôt comme suit :
>
> `printf( "%s", user_name );`

<a name="type"></a>

> [!NOTE] 
> Dans Visual Studio 2015, la famille de fonctions `printf` et `scanf` a été déclarée comme **inline** et déplacée vers les en-têtes `<stdio.h>` et `<conio.h>`. Si vous migrez du code plus ancien, vous pouvez voir l’erreur *LNK2019* en relation avec ces fonctions. Pour plus d’informations, [consultez C++ historique des modifications visuelles 2003-2015](../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="type-conversion-specifier"></a>Spécificateur de conversion de type

Le caractère spécificateur de conversion *type* précise si l’argument correspondant doit être interprété comme un caractère, une chaîne, un pointeur, un entier ou un nombre à virgule flottante. Le caractère *type*, qui est le seul champ de spécification de conversion obligatoire, apparaît après tous les champs facultatifs.

Les arguments qui suivent la chaîne de format sont interprétés en fonction du caractère *type* correspondant et du préfixe [size](#size) facultatif. Les conversions pour les types de caractères `char` et `wchar_t` sont spécifiées à l’aide de **c** ou **C**, tandis que les chaînes de caractères codés sur un octet et multioctets ou à caractères larges sont spécifiées à l’aide de **s** ou **S**, selon la fonction de mise en forme utilisée. Les arguments de caractère et de chaîne spécifiés à l’aide de **c** et **s** sont interprétés comme `char` et `char*` par les fonctions de la famille `printf` ou comme `wchar_t` et `wchar_t*` par les fonctions de la famille `wprintf`. Les arguments de caractère et de chaîne spécifiés à l’aide de **C** et **S** sont interprétés comme `wchar_t` et `wchar_t*` par les fonctions de la famille `printf` ou comme`char` et `char*` par les fonctions de la famille `wprintf`. Ce comportement est spécifique à Microsoft.

Les types d’entiers tels que `short`, `int`, `long`, `long long`et leurs `unsigned` variantes, sont spécifiés à l’aide **d**, **i**, **o**, **u**, **x**et **x**. Les types à virgule flottante, tels que `float`, `double`et `long double`, sont spécifiés à l’aide **de**, **a**, **e**, **e**, **f**, **f**, **g**et **g**. Par défaut, à moins qu’ils ne soient modifiés par un préfixe de *taille* , les arguments entiers sont forcés à `int` type, et les arguments à virgule flottante sont forcés à `double`. Sur les systèmes 64 bits, un `int` est une valeur 32 bits ; les entiers 64 bits sont donc tronqués quand ils sont mis en forme pour la sortie, à moins qu’un préfixe *size* égal à **ll** ou **I64** soit utilisé. Les types de pointeur spécifiés par **p** utilisent la taille du pointeur par défaut pour la plateforme.

> [!NOTE]
> **Spécifique à Microsoft :** Le caractère de type **Z** et le comportement des caractères de type **c**, **c**, **s**et **s** lorsqu’ils sont utilisés avec les fonctions `printf` et `wprintf`, sont des extensions Microsoft. La norme ISO C utilise systématiquement **c** et **s** pour les chaînes et les caractères étroits, et **C** et **S** pour les chaînes et les caractères larges, dans toutes les fonctions de mise en forme.

### <a name="type-field-characters"></a>Caractères du champ type

|Caractère de type|Argument|Format de sortie|
|--------------------|--------------|-------------------|
|**c**|Caractère|Quand il est utilisé avec les fonctions `printf`, spécifie un caractère codé sur un octet ; quand il est utilisé avec les fonctions `wprintf`, spécifie un caractère large.|
|**C**|Caractère|Quand il est utilisé avec les fonctions `printf`, spécifie un caractère large ; quand il est utilisé avec les fonctions `wprintf`, spécifie un caractère codé sur un octet.|
|**d**|Integer|Entier décimal signé.|
|**i**|Integer|Entier décimal signé.|
|**o**|Integer|Entier octal non signé.|
|**u**|Integer|Entier décimal non signé.|
|**x**|Integer|Entier hexadécimal non signé ; utilise « abcdef ».|
|**X**|Integer|Entier hexadécimal non signé ; utilise « ABCDEF ».|
|**e**|Virgule flottante|Valeur signée se présentant sous la forme [-]*d.dddd*__e±__*dd*\[*d*], où *d* correspond à un chiffre décimal, *dddd* à un ou plusieurs chiffres décimaux selon la précision spécifiée (ou six par défaut), et *dd*\[ *]* à deux ou trois chiffres décimaux, selon le [format de sortie](../c-runtime-library/set-output-format.md) et la taille de l’exposant.|
|**E**|Virgule flottante|Identique au format **e** sauf que l’exposant est introduit par **E** et non par **e**.|
|**f**|Virgule flottante|Valeur signée se présentant sous la forme [-]*dddd* __.__ *dddd*, où *dddd* correspond à un ou plusieurs chiffres décimaux. Le nombre de chiffres avant la virgule décimale dépend de l’ampleur du nombre, et le nombre de chiffres après la virgule décimale dépend de la précision demandée (ou six par défaut).|
|**F**|Virgule flottante|Identique au format **f**, sauf que la sortie de l’infini et NAN est en majuscules.|
|**g**|Virgule flottante|Les valeurs signées sont affichées au format **f** ou **e**, selon celui qui est le plus compact pour la valeur et la précision en question. Le format **e** est utilisé uniquement quand l’exposant de la valeur est inférieur à -4 ou supérieur ou égal à l’argument *precision*. Les zéros de droite sont tronqués et la virgule décimale apparaît uniquement si elle est suivie d'un ou plusieurs chiffres.|
|**G**|Virgule flottante|Identique au format **g**, sauf que l’exposant est introduit par **E** et non par **e** (selon le cas).|
|**a**|Virgule flottante|Valeur à virgule flottante double précision hexadécimale signée se présentant sous la forme [-]0x*h.hhhh*__p±__*dd*, où *h.hhhh* correspond aux chiffres hexadécimaux (utilisant des lettres minuscules) de la mantisse, et *dd* à un ou plusieurs chiffres de l’exposant. La précision indique le nombre de chiffres après la virgule.|
|**A**|Virgule flottante|Valeur à virgule flottante double précision hexadécimale signée se présentant sous la forme [-]0X*h.hhhh*__P±__*dd*, où *h.hhhh* correspond aux chiffres hexadécimaux (utilisant des lettres majuscules) de la mantisse, et *dd* à un ou plusieurs chiffres pour l’exposant. La précision indique le nombre de chiffres après la virgule.|
|**n**|Pointeur désignant un entier|Nombre de caractères correctement écrits jusqu'à présent dans le flux ou la mémoire tampon. Cette valeur est stockée dans l’entier dont l’adresse est fournie sous forme d’argument. La taille de l’entier désigné par le pointeur peut être contrôlée par un préfixe de spécification de la taille de l’argument. Le spécificateur **n** est désactivé par défaut ; pour plus d’informations, consultez la remarque importante sur la sécurité.|
|**p**|Type de pointeur|Affiche l’argument sous forme d’adresse composée de chiffres hexadécimaux.|
|**s**|String|Quand il est utilisé avec les fonctions `printf`, spécifie une chaîne de caractères codés sur un octet ou multioctets ; quand il est utilisé avec les fonctions `wprintf`, spécifie une chaîne de caractères larges. Les caractères s’affichent jusqu’au premier caractère Null ou jusqu’à ce que la valeur de *precision* soit atteinte.|
|**S**|String|Quand il est utilisé avec les fonctions `printf`, spécifie une chaîne de caractères larges ; quand il est utilisé avec les fonctions `wprintf`, spécifie une chaîne de caractères codés sur un octet ou multioctets. Les caractères s’affichent jusqu’au premier caractère Null ou jusqu’à ce que la valeur de *precision* soit atteinte.|
|**Z**|Structure `ANSI_STRING` ou `UNICODE_STRING`|Quand l’adresse d’une structure [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string) ou [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string) est passée comme argument, affiche la chaîne contenue dans la mémoire tampon désignée par le champ `Buffer` de la structure. Utilisez un préfixe de modificateur de *size* égal à **w** pour spécifier un argument `UNICODE_STRING`, par exemple `%wZ`. Le champ `Length` de la structure doit indiquer la longueur, en octets, de la chaîne. Le champ `MaximumLength` de la structure doit indiquer la longueur, en octets, de la mémoire tampon.<br /><br /> En règle générale, le caractère de type **Z** est utilisé uniquement dans les fonctions de débogage de pilote qui utilisent une spécification de conversion, comme `dbgPrint` et `kdPrint`.|

À compter de Visual Studio 2015, si l’argument qui correspond à un spécificateur de conversion de valeurs à virgule flottante (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) est infini, indéfini ou NaN, la sortie mise en forme est conforme à la norme C99. Ce tableau répertorie les sorties mises en forme :

|Valeur|Output|
|-----------|------------|
|infinity|`inf`|
|NaN silencieux|`nan`|
|NaN signalant|`nan(snan)`|
|Indefinite NaN|`nan(ind)`|

Ces valeurs peuvent toutes être précédées d’un signe. Si un caractère spécificateur de conversion de *type* virgule flottante est une lettre majuscule, la sortie est également en majuscules. Par exemple, si le spécificateur de format est `%F` et non `%f`, un nombre infini apparaît sous la forme `INF` et non sous la forme `inf`. Les fonctions `scanf` peuvent également analyser ces chaînes. Ces valeurs peuvent donc faire l’aller-retour par l’intermédiaire des fonctions `printf` et `scanf`.

Avant Visual Studio 2015, le CRT utilisait un autre format non standard pour la sortie des valeurs infinies, indéfinies et NaN :

|Valeur|Output|
|-----------|------------|
|+ infini|`1.#INF` *chiffres aléatoires*|
|- infini|`-1.#INF` *chiffres aléatoires*|
|Indéfini (identique à une valeur NaN silencieuse)|*chiffre* `.#IND` *chiffres aléatoires*|
|NaN|*chiffre* `.#NAN` *chiffres aléatoires*|

Toutes ces chaînes pouvaient être préfixées par un signe et mises en forme légèrement différemment en fonction de la précision et de la largeur du champ, parfois avec des effets inhabituels. Par exemple, `printf("%.2f\n", INFINITY)` afficherait `1.#J` parce que #INF serait « arrondi » avec une précision de 2 chiffres.

> [!NOTE]
> Si l’argument qui correspond à `%s` ou `%S`, ou le champ `Buffer` de l’argument qui correspond à `%Z`, est un pointeur Null, « (Null) » s’affiche.

> [!NOTE]
> Dans tous les formats exponentiels, le nombre par défaut de chiffres d’exposant affichés est de deux (trois si nécessaire). À l’aide de la fonction [_set_output_format](../c-runtime-library/set-output-format.md), vous pouvez affecter la valeur trois au nombre de chiffres affichés pour compatibilité descendante avec le code écrit pour Visual Studio 2013 et antérieur.

> [!IMPORTANT]
> Le format `%n` étant peu sécurisé par nature, il est désactivé par défaut. Si `%n` est présent dans une chaîne de format, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../c-runtime-library/parameter-validation.md). Pour activer la prise en charge de `%n`, consultez [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Directives d’indicateur

Dans une spécification de conversion, le premier champ facultatif contient des *directives d’indicateur*, zéro ou plusieurs caractères d’indicateur qui spécifient la justification de la sortie et qui contrôlent la sortie des signes, des espaces, des zéros non significatifs, des virgules décimales et des préfixes octaux et hexadécimaux. Plusieurs directives d’indicateur peuvent apparaître dans une spécification de conversion, et les caractères d’indicateur peuvent apparaître dans n’importe quel ordre.

### <a name="flag-characters"></a>Caractères d’indicateur

|Indicateur|Signification|Default|
|----------|-------------|-------------|
|**-**|Aligner à gauche le résultat selon la largeur de champ donnée.|Aligner à droite.|
|**+**|Utilisez un signe (+ ou -) pour préfixer la valeur de sortie s’il s’agit d’un type signé.|Le signe apparaît uniquement pour les valeurs signées négatives (-).|
|**0**|Si *width* est préfixé par **0**, des zéros non significatifs sont ajoutés jusqu’à ce que la largeur minimale soit atteinte. Si **0** et **-** apparaissent, le **0** est ignoré. Si **0** est spécifié pour un format entier (**i**, **u**, **x**, **X**, **o**, **d**) et qu’une spécification de précision est également présente (par exemple, `%04.d`), le **0** est ignoré. Si **0** est spécifié pour le format à virgule flottante **a** ou **A**, des zéros non significatifs sont ajoutés en préfixe à la mantisse, après le préfixe `0x` ou `0X`.|Aucun remplissage.|
|**espace** (' ')|Utilisez un espace pour préfixer la valeur de sortie si elle est signée et positive. L’espace est ignoré si l’espace et des indicateurs + apparaissent.|Aucun espace ne s’affiche.|
|**#**|Quand il est utilisé avec le format **o**, **x** ou **X**, l’indicateur **#** utilise 0, 0x ou 0X, respectivement, pour préfixer une valeur de sortie différente de zéro.|Aucun espace ne s’affiche.|
||Quand il est utilisé avec le format **e**, **E**, **f**, **F**, **a** ou **A**, l’indicateur **#** impose à la valeur de sortie de contenir une virgule décimale.|La virgule décimale apparaît uniquement si des chiffres la suivent.|
||Quand il est utilisé avec le format **g** ou **G**, l’indicateur **#** force la valeur de sortie à contenir une virgule décimale et empêche la troncature des zéros de fin.<br /><br /> Ignoré s’il est utilisé avec **c**, **d**, **i**, **u** ou **s**.|La virgule décimale apparaît uniquement si des chiffres la suivent. Les zéros de fin sont tronqués.|

<a name="width"></a>

## <a name="width-specification"></a>Spécification de largeur

Dans une spécification de conversion, le champ facultatif de spécification de largeur apparaît après n’importe quel caractère d’*indicateur*. L’argument *width* est un entier décimal non négatif qui contrôle le nombre minimal de caractères qui sont générés. Si le nombre de caractères dans la valeur de sortie est inférieur à la longueur spécifiée, des espaces sont ajoutés à gauche ou à droite des valeurs, selon que l’indicateur d’alignement à gauche ( **-** ) est spécifié ou non, jusqu’à ce que la largeur minimale soit atteinte. Si *width* est préfixé par 0, des zéros non significatifs sont ajoutés aux conversions en entiers ou en nombres à virgule flottante jusqu’à ce que la largeur minimale soit atteinte, sauf en cas de conversion en valeur infinie ou NaN.

La spécification de largeur ne provoque jamais la troncature d’une valeur. Si le nombre de caractères dans la valeur de sortie est supérieur à la largeur spécifiée, ou si *width* n’est pas spécifié, tous les caractères de la valeur sont générés, conformément à la spécification *precision*.

Si la spécification de la largeur est un astérisque (`*`), un argument `int` issu de la liste d’arguments fournit la valeur. L’argument *width* doit précéder la valeur mise en forme dans la liste des arguments, comme illustré dans l’exemple suivant :

`printf("%0*d", 5, 3);  /* 00003 is output */`

Une valeur *width* manquante ou petite dans une spécification de conversion n’entraîne pas la troncation d’une valeur de sortie. Si le résultat d’une conversion est plus large que la valeur *width*, le champ peut être développé pour contenir le résultat de la conversion.

<a name="precision"></a>

## <a name="precision-specification"></a>Spécification de précision

Dans une spécification de conversion, le troisième champ facultatif concerne la spécification de précision. Il se compose d’un point (.) suivi d’un entier décimal non négatif qui, selon le type de conversion, spécifie le nombre de caractères de chaîne, le nombre de décimales ou le nombre de chiffres significatifs à générer.

Contrairement à la spécification de largeur, la spécification de précision peut entraîner la troncation de la valeur de sortie ou l’arrondi d’une valeur à virgule flottante. Si vous spécifiez 0 comme*precision* et que la valeur à convertir est 0, vous n’obtenez aucune sortie de caractères, comme illustré dans cet exemple :

`printf( "%.0d", 0 );      /* No characters output */`

Si la spécification de précision est un astérisque (\*), un argument `int` issu de la liste d’arguments fournit la valeur. Dans la liste d’arguments, l’argument *precision* doit précéder la valeur mise en forme, comme illustré dans cet exemple :

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Le caractère *type* détermine soit l’interprétation de *precision*, soit la précision par défaut quand *precision* est omis, comme illustré dans le tableau suivant.

### <a name="how-precision-values-affect-type"></a>Impact des valeurs de précision sur le type

|Type|Signification|Default|
|----------|-------------|-------------|
|**a**, **A**|La précision indique le nombre de chiffres après la virgule.|La précision par défaut s’élève à 13. Si la précision a la valeur 0, aucune virgule décimale n’est imprimée, sauf si l’indicateur **#** est utilisé.|
|**c**, **C**|La précision n’a aucun effet.|Le caractère est imprimé.|
|**d**, **i**, **o**, **u**, **x**, **X**|La précision indique le nombre minimal de chiffres à imprimer. Si le nombre de chiffres dans l’argument est inférieur à *precision*, la valeur de sortie est remplie à gauche de zéros. La valeur n’est pas tronquée quand le nombre de chiffres dépasse *precision*.|La précision par défaut s’élève à 1.|
|**e**, **E**|La précision indique le nombre de chiffres à imprimer après la virgule décimale. Le dernier chiffre imprimé est arrondi.|La précision par défaut s’élève à 6. Si *precision* a la valeur 0 ou si le point (.) apparaît sans être suivi d’un nombre, aucune virgule décimale n’est imprimée.|
|**f**, **F**|La valeur de précision indique le nombre de chiffres après la virgule décimale. Si une virgule décimale apparaît, au moins un chiffre apparaît devant. La valeur est arrondie au nombre approprié de chiffres.|La précision par défaut s’élève à 6. Si *precision* a la valeur 0 ou si le point (.) apparaît sans être suivi d’un nombre, aucune virgule décimale n’est imprimée.|
|**g**, **G**|La précision indique le nombre maximal de chiffres significatifs imprimés.|Six chiffres significatifs sont imprimés et tous les zéros de fin sont tronqués.|
|**s**, **S**|La précision indique le nombre maximal de caractères à imprimer. Les caractères au-delà de *precision* ne sont pas imprimés.|Les caractères sont imprimés jusqu’à ce qu’un caractère Null soit rencontré.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Spécification de taille d’argument

Dans une spécification de conversion, le champ *size* est un modificateur de longueur d’argument pour le spécificateur de conversion *type*. Les préfixes de champ *size* du champ *type*, à savoir **hh**, **h**, **j**, **l** (L minuscule), **L**, **ll**, **t**, **w**, **z**, **I** (i majuscule), **I32** et **I64**, spécifient la « taille » de l’argument correspondant (long ou court, 32 bits ou 64 bits, caractère sur un octet ou large), selon le spécificateur de conversion qu’ils modifient. Ces préfixes de taille sont utilisés avec les caractères de *type* dans les familles `printf` et `wprintf` de fonctions pour spécifier l’interprétation des tailles d’argument, comme illustré dans le tableau suivant. Le champ *size* est facultatif pour certains types d’arguments. Si aucun préfixe de taille n’est spécifié, le formateur consomme les arguments d’entier (par exemple `char`, `short`, `int`, `long` signé ou non signé, ainsi que les types d’énumération) en tant que types `int` 32 bits, tandis que les arguments à virgule flottante `float`, `double` et `long double` sont consommés en tant que types `double` 64 bits. Ce comportement correspond aux règles de promotion d’argument par défaut pour les listes d’arguments de variable. Pour plus d’informations sur la promotion d’argument, consultez Ellipses et arguments par défaut dans [Expressions de suffixe](../cpp/postfix-expressions.md). Sur les systèmes 32 bits et 64 bits, la spécification de conversion d’un argument d’entier 64 bits doit inclure un préfixe de taille **ll** ou **I64**. Sinon, le comportement du formateur n'est pas défini.

Certains types sont de tailles différentes en code 32 bits et 64 bits. Par exemple, la longueur de `size_t` est 32 bits dans le code compilé pour x86, contre 64 bits dans le code compilé pour x64. Pour créer un code de mise en forme indépendant de la plateforme pour les types de largeur variable, vous pouvez utiliser un modificateur de taille d’argument de largeur variable. Vous pouvez également utiliser un modificateur de taille d’argument 64 bits et promouvoir explicitement le type d’argument de largeur variable à 64 bits. Spécifique à Microsoft, le modificateur de taille d’argument **I** (i majuscule) gère les arguments entiers de largeur variable. Toutefois, nous vous recommandons d’utiliser les modificateurs **j**, **t** et **z** spécifiques au type à des fins de portabilité.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Préfixes de taille pour les spécificateurs de type de format printf et wprintf

|Pour spécifier|Utilisez le préfixe|Avec le spécificateur de type|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x** ou **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x** ou **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x** ou **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x** ou **X**|
|`intmax_t`<br />`uintmax_t`|**j** ou **I64**|**d**, **i**, **o**, **u**, **x** ou **X**|
|`long double`|**l** (L minuscule) ou **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g** ou **G**|
|`long int`<br />`long unsigned int`|**l** (L minuscule)|**d**, **i**, **o**, **u**, **x** ou **X**|
|`long long int`<br />`unsigned long long int`|**ll** (LL minuscules)|**d**, **i**, **o**, **u**, **x** ou **X**|
|`ptrdiff_t`|**t** ou **I** (i majuscule)|**d**, **i**, **o**, **u**, **x** ou **X**|
|`size_t`|**z** ou **I** (i majuscule)|**d**, **i**, **o**, **u**, **x** ou **X**|
|Caractère codé sur un octet|**h**|**c** ou **C**|
|Caractère large|**l** (L minuscule) ou **w**|**c** ou **C**|
|Chaîne de caractères codés sur un octet|**h**|**s**, **S** ou **Z**|
|Chaîne de caractères larges|**l** (L minuscule) ou **w**|**s**, **S** ou **Z**|

Les types `ptrdiff_t` et `size_t` sont `__int32` et `unsigned __int32` sur les plateformes 32 bits, et `__int64` ou `unsigned __int64` sur les plateformes 64 bits. Les préfixes de taille **I** (i majuscule), **j**, **t** et **z** acceptent la largeur correcte des arguments pour la plateforme.

Dans Visual C++, bien que `long double` soit un type distinct, il possède la même représentation interne que `double`.

Un spécificateur de type **hc** ou **hC** est synonyme de **c** dans les fonctions `printf` et de **C** dans les fonctions `wprintf`. Un spécificateur de type **lc**, **lC**, **wc** ou **wC** est synonyme de **C** dans les fonctions `printf` et de **c** dans les fonctions `wprintf`. Un spécificateur de type **hs** ou **hS** est synonyme de **s** dans les fonctions `printf` et de **S** dans les fonctions `wprintf`. Un spécificateur de type **ls**, **lS**, **ws** ou **wS** est synonyme de **S** dans les fonctions `printf` et de **s** dans les fonctions `wprintf`.

> [!NOTE]
> **Spécifique à Microsoft :** Les préfixes de modificateur de taille d’argument **i** (i majuscule), **i32**, **I64**et **w** sont des extensions Microsoft et ne sont pas compatibles ISO C. Le préfixe **h** utilisé avec des données de type `char` et le préfixe**l** (L minuscule) utilisé avec des données de type `double` sont des extensions Microsoft.

## <a name="see-also"></a>Voir aussi

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[Paramètres positionnels printf_p](../c-runtime-library/printf-p-positional-parameters.md)
