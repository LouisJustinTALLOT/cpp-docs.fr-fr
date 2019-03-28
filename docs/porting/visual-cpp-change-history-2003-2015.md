---
title: Historique des modifications de Visual C++ entre 2003 et 2015
ms.date: 08/30/2017
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: 20920a5f1a1cdf2a4e10263a7b1de3010f24f9c0
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58329037"
---
# <a name="visual-c-change-history-2003---2015"></a>Historique des modifications de Visual C++ entre 2003 et 2015

Cet article décrit toutes les modifications avec rupture dans Visual Studio 2015 en remontant jusqu’à Visual Studio 2003 et, dans cet article, les termes « nouveau comportement » ou « maintenant » font référence à Visual Studio 2015 et versions ultérieures. Les termes « ancien comportement » et « avant » font référence à Visual Studio 2013 et aux versions antérieures.

Pour plus d’informations sur Visual Studio 2017, consultez [Nouveautés de Visual C++ dans Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) et [Améliorations de la conformité de Visual C++ dans Visual Studio 2017](../cpp-conformance-improvements-2017.md).

> [!NOTE]
> Aucune modification importante n’a été apportée au niveau des binaires entre Visual Studio 2015 et Visual Studio 2017.

Quand vous effectuez une mise à niveau avec une nouvelle version de Visual Studio, vous pouvez rencontrer des erreurs de compilation et/ou d’exécution dans du code qui pouvait auparavant être compilé et exécuté correctement. Les modifications introduites dans la nouvelle version qui génèrent de tels problèmes sont appelées *modifications avec rupture*et elles sont généralement requises par des modifications apportées à la norme du langage C++, aux signatures des fonctions ou à la disposition des objets en mémoire.

Pour éviter les erreurs d’exécution qui sont difficiles à détecter et diagnostiquer, nous vous recommandons de ne jamais établir de lien statique à des binaires compilés à l’aide d’une version différente du compilateur. En outre, lorsque vous mettez à niveau un projet EXE ou DLL, veillez à mettre à niveau les bibliothèques auxquelles il est lié. Ne transmettez pas des types de bibliothèques C++ standard ou Runtime C (CRT) entre des fichiers binaires (notamment des DLL) compilés à l’aide de différentes versions du compilateur. Pour plus d’informations, consultez [Erreurs potentielles de passage d’objets CRT entre frontières DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Ne rédigez jamais du code dépendant d’une disposition particulière pour un objet qui n’est pas une interface COM ou un objet POD. Si vous rédigez un tel code, vous devez vous assurer qu'il fonctionne après la mise à niveau. Pour plus d’informations, consultez [Portabilité aux limites ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).

En outre, les améliorations suivies de la conformité du compilateur peuvent parfois modifier la façon dont le compilateur comprend votre code source existant. Par exemple, vous pouvez être confronté à des erreurs nouvelles ou différentes pendant la génération, ou même à des différences de comportement dans le code qui auparavant était généré et paraissait s’exécuter correctement. Même s’il ne s’agit pas là de changements cassants tels que ceux présentés dans ce document, vous devrez peut-être apporter des changements à votre code source pour résoudre ces problèmes :

- [Modifications avec rupture de la bibliothèque C Runtime (CRT)](#BK_CRT)

- [Modifications avec rupture de la bibliothèque C++ standard](#BK_STL)

- [Modifications avec rupture des bibliothèques MFC et ATL](#BK_MFC)

- [Modifications avec rupture du runtime d’accès concurrentiel](#BK_ConcRT)

## <a name="VC_2015"></a> Modifications de la mise en conformité de Visual C++ 2015

###  <a name="BK_CRT"></a> Bibliothèque Runtime C (CRT)

#### <a name="general-changes"></a>Modifications générales

- **Fichiers binaires refactorisés**

   La bibliothèque CRT a été refactorisée en deux fichiers binaires différents, la bibliothèque Universal CRT (ucrtbase), qui contient la plupart des fonctionnalités standard, et une bibliothèque runtime VC (vcruntime). La bibliothèque vcruntime contient les fonctionnalités associées au compilateur, telles que la gestion des exceptions, et les intrinsèques. Si vous utilisez les paramètres de projet par défaut, cette modification n’a aucune incidence, car l’éditeur de liens utilise automatiquement les nouvelles bibliothèques par défaut. Si vous avez défini, dans l’**éditeur de liens**, la propriété **Ignorer toutes les bibliothèques par défaut** du projet sur **Oui**, ou si vous utilisez l’option `/NODEFAULTLIB` de l’éditeur de liens sur la ligne de commande, vous devez mettre à jour votre liste de bibliothèques (dans la propriété **Dépendances supplémentaires**) pour inclure les nouvelles bibliothèques refactorisées. Remplacez l'ancienne bibliothèque CRT (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib) par les bibliothèques refactorisées équivalentes. Pour chacune des deux bibliothèques refactorisées, il existe des versions statiques (.lib) et dynamiques (.dll), ainsi que des versions release (sans suffixe) et debug (avec le suffixe « d »). Les versions dynamiques ont une bibliothèque d'importation avec laquelle vous établissez une liaison. Les deux bibliothèques refactorisées sont Universal CRT, en particulier ucrtbase.dll ou ucrtbase.lib, ucrtbased.dll ou ucrtbased.lib, et la bibliothèque runtime VC, libvcruntime.lib, vcruntime*version*.dll, libvcruntimed.lib et vcruntimed*version*.dll. La *version* dans Visual Studio 2015 et Visual Studio 2017 est 140. Consultez [Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<locale.h>

- **localeconv**

   La fonction [localeconv](../c-runtime-library/reference/localeconv.md) déclarée dans locale.h fonctionne à présent correctement quand les [paramètres régionaux par thread](../parallel/multithreading-and-locales.md) sont activés. Dans les versions précédentes de la bibliothèque, cette fonction retournait les données `lconv` pour les paramètres régionaux globaux, et non pour les paramètres régionaux du thread.

   Si vous utilisez des paramètres régionaux par thread, vous devez vérifier votre utilisation de `localeconv`. Si votre code part du principe que les données `lconv` retournées sont pour les paramètres régionaux globaux, vous devez le corriger.

#### <a name="mathh"></a>\<math.h>

- **Surcharges C++ des fonctions mathématiques de la bibliothèque**

   Dans les versions précédentes, \<math.h> définissait certaines surcharges C++ pour les fonctions mathématiques de la bibliothèque. Le reste des surcharges se trouvaient dans l’en-tête \<cmath>. Le code incluant uniquement \<math.h> pouvait rencontrer des problèmes de résolution de surcharge de fonction. À présent, toutes les surcharges C++ ont été supprimées de \<math.h> et sont présentes uniquement dans \<cmath>.

   Pour résoudre les erreurs, incluez \<cmath> pour obtenir les déclarations des fonctions qui ont été supprimées de \<math.h>. Ces fonctions ont été déplacées :

  - `double abs(double)` et `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - Versions `float` et `long double` des fonctions à virgule flottante `acos`, `acosh`, `asin`, `asinh`, `atan`, `atanh`, `atan2`, `cbrt`, `ceil`, `copysign`, `cos`, `cosh`, `erf`, `erfc`, `exp`, `exp2`, `expm1`, `fabs`, `fdim`, `floor`, `fma`, `fmax`, `fmin`, `fmod`, `frexp`, `hypot`, `ilogb`, `ldexp`, `lgamma`, `llrint`, `llround`, `log`, `log10`, `log1p`, `log2`, `lrint`, `lround`, `modf`, `nearbyint`, `nextafter`, `nexttoward`, `remainder`, `remquo`, `rint`, `round`, `scalbln`, `scalbn`, `sin`, `sinh`, `sqrt`, `tan`, `tanh`, `tgamma` et `trunc`

  Si vous avez du code qui utilise `abs` avec un type à virgule flottante incluant uniquement l’en-tête \<math.h>, les versions à virgule flottante ne sont plus disponibles. L’appel se traduit à présent par `abs(int)`, même avec un argument à virgule flottante, ce qui génère l’erreur :

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Le correctif pour cet avertissement consiste à remplacer l’appel à `abs` par une version à virgule flottante de `abs`, comme `fabs` pour un argument double ou `fabsf` pour un argument float, ou à inclure l’en-tête \<cmath> et à continuer d’utiliser `abs`.

- **Conformité en matière de virgule flottante**

   De nombreuses modifications ont été apportées à la bibliothèque mathématique pour améliorer la conformité aux normes IEEE-754 et C11 annexe F en ce qui concerne les entrées de cas spéciaux telles que les valeurs NaN et les infinis. Par exemple, les entrées NaN silencieuses, qui étaient souvent considérées comme des erreurs dans les versions antérieures de la bibliothèque, ne sont plus traitées comme des erreurs. Consultez la [norme IEEE 754](https://standards.ieee.org/standard/754-2008.html) et l’annexe F de la [norme C11](http://www.iso-9899.info/wiki/The_Standard).

   Ces modifications ne provoqueront pas d'erreurs de compilation, mais peuvent entraîner des changements de comportement des programmes (plus conforme à la norme).

- **FLT_ROUNDS**

   Dans Visual Studio 2013, la macro FLT_ROUNDS s'étendait à une expression constante, ce qui était incorrect car le mode d'arrondi est configurable à l'exécution, par exemple, en appelant fesetround. La macro FLT_ROUNDS est à présent dynamique et reflète fidèlement le mode d'arrondi actuel.

#### <a name="new-and-newh"></a>\<new> et \<new.h>

- **new et delete**

   Dans les versions antérieures de la bibliothèque, les fonctions opérateur new et delete définies par l'implémentation étaient exportées à partir de la DLL de la bibliothèque runtime (par exemple, msvcr120.dll). Ces fonctions opérateur sont à présent toujours liées statiquement dans vos fichiers binaires, même si vous utilisez les DLL de la bibliothèque runtime.

   Il ne s’agit pas d’un changement cassant pour du code natif ou mixte (`/clr`). Toutefois, pour du code compilé avec [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md), ce changement peut entraîner l’échec de la compilation de votre code. Si vous compilez du code avec `/clr:pure`, vous devrez peut-être ajouter `#include <new>` ou `#include <new.h>` pour éviter les erreurs de build causées par cette modification. L’option `/clr:pure` est dépréciée dans Visual Studio 2015 et non prise en charge dans Visual Studio 2017. Le code qui doit être « pur » doit être déplacé vers C#.

#### <a name="processh"></a>\<process.h>

- **_beginthread et _beginthreadex**

   Les fonctions [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) et [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) contiennent à présent une référence au module dans lequel la procédure de thread est définie pour la durée du thread. Cela permet de garantir que les modules ne sont pas déchargés tant qu’un thread n’a pas été exécuté jusqu’à la fin.

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start et types référence**

   Lors de la compilation de code C++, [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) valide désormais que l’argument qui lui est transmis n’est pas de type référence. Les arguments de type référence sont interdits par la norme C++.

#### <a name="stdioh-and-conioh"></a>\<stdio.h> et \<conio.h>

- **Les familles de fonctions printf et scanf sont maintenant définies inline.**

   Les définitions de toutes les fonctions `printf` et `scanf` ont été placées inline dans \<stdio.h>, \<conio.h> et les autres en-têtes CRT. Ce changement cassant conduit à une erreur de l’éditeur de liens (LNK2019, symbole externe non résolu) pour tous les programmes ayant déclaré ces fonctions localement sans inclure les en-têtes CRT appropriés. Si possible, mettez à jour le code pour inclure les en-têtes CRT (c’est-à-dire, ajouter `#include <stdio.h>`) et les fonctions inline, mais si vous ne voulez pas modifier votre code pour inclure ces fichiers d’en-tête, une autre solution consiste à ajouter une bibliothèque supplémentaire à votre entrée d’éditeur de liens, legacy_stdio_definitions.lib.

   Pour ajouter cette bibliothèque à votre entrée d’éditeur de liens dans l’environnement IDE, ouvrez le menu contextuel du nœud du projet, choisissez **Propriétés**, puis dans la boîte de dialogue **Propriétés du projet**, choisissez **Éditeur de liens**. Ensuite, modifiez **l’entrée de l’éditeur de liens** afin d’ajouter `legacy_stdio_definitions.lib` à la liste délimitée par des points-virgules.

   Si votre projet est lié à des bibliothèques statiques qui ont été compilées avec une version de Visual Studio antérieure à 2015, l’éditeur de liens peut signaler un symbole externe non résolu. Ces erreurs peuvent référencer des définitions internes pour `_iob`, `_iob_func`, ou des importations associées pour certaines fonctions \<stdio.h> de la forme _imp_\*. Microsoft recommande de recompiler toutes les bibliothèques statiques avec la dernière version des bibliothèques et du compilateur C++ quand vous mettez à niveau un projet. Si la bibliothèque est une bibliothèque tierce dont la source n’est pas disponible, vous devez demander un fichier binaire mis à jour auprès de la tierce partie ou encapsuler votre utilisation de cette bibliothèque dans une DLL distincte que vous compilez à l’aide de l’ancienne version des bibliothèques et du compilateur.

    > [!WARNING]
    > Si vous établissez une liaison avec le Kit de développement logiciel (SDK) Windows 8.1 ou version antérieure, vous pouvez rencontrer ces erreurs de symbole externe non résolues. Dans ce cas, vous devez résoudre l'erreur en ajoutant legacy_stdio_definitions.lib à l'entrée de l'éditeur de liens, comme décrit précédemment.

   Pour résoudre les erreurs de symboles non résolus, vous pouvez essayer d’utiliser [dumpbin.exe](../build/reference/dumpbin-reference.md) pour examiner les symboles définis dans un fichier binaire. Essayez d'utiliser la ligne de commande ci-dessous pour afficher les symboles définis dans une bibliothèque.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **gets et _getws**

   Les fonctions [gets](../c-runtime-library/gets-getws.md) et [_getws](../c-runtime-library/gets-getws.md) ont été supprimées. La fonction gets a été supprimée de la Bibliothèque standard du C dans C11, car elle ne peut pas être utilisée en toute sécurité. La fonction _getws était une extension Microsoft équivalente à gets, mais pour les chaînes étendues. Comme alternatives à ces fonctions, envisagez d’utiliser [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md) et [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets et _cgetws**

   Les fonctions [_cgets](../c-runtime-library/cgets-cgetws.md) et [_cgetws](../c-runtime-library/cgets-cgetws.md) ont été supprimées. Comme alternatives à ces fonctions, envisagez d’utiliser [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) et [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Formatage de valeurs NaN et infinies**

   Dans les versions précédentes, les valeurs infinies et NaN étaient formatées à l’aide d’un ensemble de chaînes de sentinelles propres à MSVC.

  - Infinity: 1.#INF

  - Quiet NaN: 1.#QNAN

  - Signaling NaN: 1.#SNAN

  - Indefinite NaN: 1.#IND

  Tous ces formats pouvaient être précédés d’un signe et mis en forme un peu différemment en fonction de la précision et de la largeur de champ (parfois avec des effets inhabituels, par exemple : `printf("%.2f\n", INFINITY)` affichait 1.#J, car #INF était « arrondi » avec une précision de deux chiffres). C99 a introduit de nouvelles spécifications sur la façon dont les valeurs infinies et NaN devaient être formatées. À présent, l’implémentation de MSVC est conforme à ces spécifications. Les nouvelles chaînes sont :

  - Infinity: inf

  - Quiet NaN: nan

  - Signaling NaN: nan(snan)

  - Indefinite NaN: nan(ind)

  Elles peuvent toutes être précédées d'un signe. Si un spécificateur de format majuscule est utilisé (%F au lieu de %f), les chaînes apparaissent en majuscules (`INF` au lieu de `inf`), comme cela est requis.

  Les fonctions [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) ont été modifiées pour analyser ces nouvelles chaînes, afin que ces chaînes effectuent un aller-retour via `printf` et `scanf`.

- **Formatage et analyse avec virgule flottante**

   De nouveaux algorithmes de formatage et d'analyse de virgule flottante ont été introduits pour améliorer l'exactitude. Cette modification affecte les familles de fonctions [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) et [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), ainsi que des fonctions telles que [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Les anciens algorithmes de formatage généraient un nombre limité de chiffres, puis remplissaient les emplacements décimaux restants par des zéros. Ils pouvaient généralement générer des chaînes qui revenaient à la valeur à virgule flottante d’origine, mais cette solution n’était pas idéale si vous souhaitiez la valeur exacte (ou sa représentation décimale la plus proche). Les nouveaux algorithmes de formatage génèrent autant de chiffres que cela est nécessaire pour représenter la valeur (ou pour satisfaire à la précision spécifiée). Comme exemple illustrant cette amélioration, considérons les résultats obtenus en affichant une grande puissance de deux :

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   Sortie du travail :

    ```Output
    1208925819614629200000000
    ```

   Nouvelle sortie :

    ```Output
    1208925819614629174706176
    ```

   Les anciens algorithmes d'analyse prenaient en compte un maximum de 17 chiffres significatifs dans la chaîne d'entrée et ignoraient les chiffres restants. Cette approche suffit pour générer une approximation proche de la valeur représentée par la chaîne et le résultat est généralement très proche du résultat correctement arrondi. La nouvelle implémentation prend en compte tous les chiffres présents et génère le résultat correctement arrondi pour toutes les entrées (jusqu'à 768 chiffres). En outre, ces fonctions respectent désormais le mode d'arrondi (contrôlable via fesetround).  Il s’agit potentiellement d’un comportement cassant, car les fonctions peuvent générer des résultats différents. Les nouveaux résultats sont toujours plus exacts que les anciens.

- **Analyse de virgule flottante de valeurs hexadécimales et infinies/NaN**

   Les algorithmes d’analyse de virgule flottante analyseront à présent les chaînes hexadécimales à virgule flottante (telles que celles générées par les spécificateurs de format printf %a et %A) et toutes les chaînes infinies et NaN générées par les fonctions `printf`, comme décrit ci-dessus.

- **Remplissage à l’aide de zéros de %A et %a**

   Les spécificateurs de format %a et %A formatent un nombre à virgule flottante sous la forme d'une mantisse hexadécimale et d'un exposant binaire. Dans les versions antérieures, les fonctions `printf` affichaient des zéros supplémentaires, ce qui était incorrect. Par exemple, `printf("%07.0a\n", 1.0)` affichait 00x1p+0 au lieu de 0x01p+0. Ce défaut a été résolu.

- **Précision de %A et %a**

   La précision par défaut des spécificateurs de format %A et %a était de 6 dans les versions antérieures de la bibliothèque. La précision par défaut est désormais de 13 pour être conforme à la norme du C.

   Il s'agit d'un changement de comportement d'exécution dans la sortie de n'importe quelle fonction qui utilise une chaîne de format avec %A ou %a. Selon l'ancien comportement, la sortie utilisant le spécificateur %A peut être « 1,1A2B3Cp+111 ». À présent, la sortie pour la même valeur est « 1,1A2B3C4D5E6F7p+111 ». Pour obtenir l'ancien comportement, vous pouvez spécifier la précision, par exemple, %.6A. Consultez [Spécifications de précision](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Spécificateur %F**

   Le spécificateur de format/conversion %F est maintenant pris en charge. Il est fonctionnellement équivalent au spécificateur de format %f, si ce n’est que les valeurs infinies et NaN sont formatées au moyen de lettres majuscules.

   Dans les versions précédentes, l'implémentation analysait F et N en tant que modificateurs de longueur. Ce comportement datait du temps des espaces d'adressage segmentés : ces modificateurs de longueur servaient à indiquer des pointeurs proches et lointains, respectivement, comme dans %Fp ou %Ns. Ce comportement a été supprimé. %F est désormais traité comme le spécificateur de format %F. Si vous rencontrez %N, il est maintenant traité comme un paramètre non valide.

- **Mise en forme des exposants**

   Les spécificateurs de format %e et %E formatent un nombre à virgule flottante sous la forme d'une mantisse décimale et d'un exposant. Les spécificateurs de format %g et %G formatent également les nombres sous cette forme, dans certains cas. Dans les versions précédentes, le CRT générait toujours des chaînes avec des exposants à trois chiffres. Par exemple, `printf("%e\n", 1.0)` affichait 1,000000e+000, ce qui était incorrect. le langage C requiert que si l’exposant peut être représenté uniquement avec un ou deux chiffres, seulement deux chiffres doivent être affichés.

   Dans Visual Studio 2005, un commutateur de conformité globale a été ajouté : [_set_output_format](../c-runtime-library/set-output-format.md). Un programme peut appeler cette fonction avec l'argument _TWO_DIGIT_EXPONENT pour permettre un affichage d'exposant conforme. Le comportement par défaut a été remplacé par le mode d'affichage d'exposant conforme aux normes.

- **Validation des chaînes de format**

   Dans les versions précédentes, les fonctions `printf` et `scanf` acceptaient silencieusement de nombreuses chaînes de format non valides, parfois avec des effets inhabituels. Par exemple, %hlhlhld était traité comme %d. Toutes les chaînes de format non valides sont désormais traitées comme des paramètres non valides.

- **Validation des chaînes de mode fopen**

   Dans les versions précédentes, la famille `fopen` de fonctions acceptait silencieusement certaines chaînes de mode non valides (telles que `r+b+`). Les chaînes de mode non valides sont désormais détectées et traitées comme des paramètres non valides.

- **Mode _O_U8TEXT**

   La fonction [_setmode](../c-runtime-library/reference/setmode.md) signale désormais correctement le mode pour les flux ouverts en mode _O_U8TEXT. Dans les versions précédentes de la bibliothèque, elle signalait ces flux de données comme étant ouverts dans _O_WTEXT.

   Il s'agit d'une modification avec rupture si votre code interprète le mode _O_WTEXT pour des flux dont l'encodage est UTF-8. Si votre application ne prend pas en charge UTF_8, envisagez d'ajouter la prise en charge pour cet encodage de plus en plus courant.

- **snprintf et vsnprintf**

   Les fonctions [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) et [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) sont à présent implémentées. Du code plus ancien fournissait souvent des versions macro de définitions de ces fonctions, car elles n’étaient pas implémentées par la bibliothèque CRT, mais elles ne sont plus nécessaires dans les versions plus récentes. Si [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) ou [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) est défini comme macro avant l’inclusion de \<stdio.h>, la compilation échoue désormais avec une erreur qui indique où la macro a été définie.

   Normalement, le correctif de ce problème consiste à supprimer toutes les déclarations de `snprintf` ou `vsnprintf` dans le code utilisateur.

- **tmpnam génère des noms de fichiers utilisables**

   Dans les versions précédentes, les fonctions `tmpnam` et `tmpnam_s` généraient des noms de fichiers à la racine du lecteur (par exemple, \sd3c.). Ces fonctions génèrent désormais des chemins d'accès de noms de fichiers utilisables dans un répertoire temporaire.

- **Encapsulation FILE**

   Dans les versions précédentes, le type FILE complet était défini publiquement dans \<stdio.h>, si bien qu’il était possible pour le code utilisateur d’accéder à un type FILE et de modifier ses éléments internes. La bibliothèque a été modifiée pour masquer les détails d’implémentation. Dans le cadre de cette modification, le type FILE tel que défini dans \<stdio.h> est désormais un type opaque et ses membres sont inaccessibles de l’extérieur de la bibliothèque CRT elle-même.

- **_outp et _inp**

   Les fonctions [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md) et [_inpd](../c-runtime-library/inp-inpw-inpd.md) ont été supprimées.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>, \<malloc.h> et \<sys/stat.h>

- **strtof et wcstof**

   Les fonctions `strtof` et `wcstof` ne pouvaient pas assigner la valeur ERANGE à `errno` quand la valeur n’était pas représentable en valeur float. Cette erreur concernait uniquement ces deux fonctions, et les fonctions `strtod`, `wcstod`, `strtold` et `wcstold` n’étaient pas impactées. Ce problème a été résolu, et est un changement cassant du runtime.

- **Fonctions d’allocation alignée**

   Dans les versions précédentes, les fonctions d’allocation alignée (`_aligned_malloc`, `_aligned_offset_malloc`, etc.) acceptaient silencieusement les demandes pour un bloc avec un alignement de 0. L’alignement demandé doit être une puissance de deux, ce qui n’est pas le cas de zéro. Un alignement demandé de 0 est désormais traité comme un paramètre non valide. Ce problème a été résolu, et est un changement cassant du runtime.

- **Fonctions de segment de mémoire**

   Les fonctions `_heapadd`, `_heapset` et `_heapused` ont été supprimées. Ces fonctions ne fonctionnaient plus depuis que la bibliothèque CRT a été mise à jour pour utiliser le segment de mémoire de Windows.

- **smallheap**

   L’option de lien `smallheap` a été supprimée. Consultez [Options de lien](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   La signature de la fonction `wcstok` a été modifiée pour correspondre à ce qui est requis par la norme C. Dans les versions précédentes de la bibliothèque, la signature de cette fonction était :

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Elle utilisait un contexte par thread interne pour suivre l’état entre les appels, comme c’est le cas pour `strtok`. La fonction a maintenant la signature `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)`, et exige que l’appelant passe le contexte à la fonction comme troisième argument.

   Une nouvelle fonction `_wcstok` a été ajoutée avec l’ancienne signature pour faciliter le portage. Quand vous compilez du code C++, il existe également une surcharge inline de `wcstok` qui a l’ancienne signature. Cette surcharge est déclarée comme déconseillée. Dans le code C, vous pouvez définir _CRT_NON_CONFORMING_WCSTOK pour que `_wcstok` soit utilisé à la place de `wcstok`.

#### <a name="timeh"></a>\<time.h>

- **horloge**

   Dans les versions précédentes, la fonction [clock](../c-runtime-library/reference/clock.md) était implémentée à l’aide de l’API Windows [GetSystemTimeAsFileTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). Avec cette implémentation, la fonction clock était sensible à l'heure système et n'était donc pas nécessairement unitone. La fonction clock a été réimplémentée en tant que [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) . Elle est désormais monotone.

- **fstat et _utime**

   Dans les versions précédentes, les fonctions [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) et [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) géraient l’heure d’été de façon incorrecte. Avant Visual Studio 2013, toutes ces fonctions ajustaient de façon incorrecte les heures à l'heure d'hiver comme si les heures d'été étaient prises en compte.

   Dans Visual Studio 2013, le problème a été résolu dans la famille de fonctions **_stat**, mais il restait des problèmes similaires dans les familles de fonctions **fstat** et **_utime**. Ce correctif partiel a conduit à des problèmes en raison de l’incohérence entre les fonctions. Des corrections ont été apportées aux familles de fonctions **fstat** et **_utime**. Maintenant, toutes ces fonctions gèrent l’heure d’été de façon correcte et cohérente.

- **asctime**

   Dans les versions précédentes, la fonction [asctime](../c-runtime-library/reference/asctime-wasctime.md) complétait les jours à un chiffre avec un zéro non significatif. Exemple : `Fri Jun 06 08:00:00 2014`. La spécification exige que ces jours soient complétés par un espace à gauche, comme dans `Fri Jun  6 08:00:00 2014`. Ce problème a été résolu.

- **strftime et wcsftime**

   Les fonctions `strftime` et `wcsftime` prennent désormais en charge les spécificateurs de format %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u et %V. En outre, les modificateurs E et O sont analysés mais ignorés.

   Le spécificateur de format %c est spécifié comme générant une « représentation appropriée de date et heure » pour les paramètres régionaux actuels. Dans les paramètres régionaux C, cette représentation doit être identique à `%a %b %e %T %Y`, la même forme que celle produite par `asctime`. Dans les versions précédentes, le spécificateur de format %c formatait de façon incorrecte les heures à l’aide d’une représentation `MM/DD/YY HH:MM:SS`. Ce problème a été résolu.

- **timespec et TIME_UTC**

   L’en-tête \<time.h> définit à présent le type `timespec` et la fonction `timespec_get` issus de la norme C11. En outre, la macro TIME_UTC, à utiliser avec la fonction `timespec_get`, est maintenant définie. Il s’agit d’un changement cassant pour le code qui a une définition en conflit pour l’un de ces identificateurs.

- **CLOCKS_PER_SEC**

   La macro CLOCKS_PER_SEC se développe désormais en un entier de type `clock_t`, comme cela est requis par le langage C.

####  <a name="BK_STL"></a> Bibliothèque C++ standard

Pour activer les nouvelles optimisations et vérifications de débogage, l'implémentation Visual Studio de la bibliothèque C++ standard interrompt intentionnellement la compatibilité binaire d'une version à la suivante. Par conséquent, lorsque la bibliothèque C++ standard est utilisée, les fichiers objets et les bibliothèques statiques qui sont compilés à l'aide de différentes versions ne peuvent pas être combinés en un seul binaire (EXE ou DLL), et les objets de la bibliothèque C++ standard ne peuvent pas être transmis entre des binaires compilés à l'aide de différentes versions. Une telle combinaison entraîne des erreurs de l'éditeur de liens concernant des incompatibilités _MSC_VER. (_MSC_VER est la macro contenant la version majeure du compilateur. Par exemple, 1800 pour Visual Studio 2013.) Cette vérification ne peut pas détecter les combinaisons de DLL et ne peut pas détecter les combinaisons impliquant Visual Studio 2008 ou version antérieure.

- **Fichiers include de bibliothèque C++ standard**

   Certaines modifications ont été apportées à la structure include dans les en-têtes de bibliothèque C++ standard. Les en-têtes de la bibliothèque C++ standard sont autorisés à s’inclure mutuellement de façons non spécifiées. En général, vous devez écrire votre code afin qu’il inclue soigneusement tous les en-têtes dont il a besoin conformément à la norme C++, et ne s’appuie pas sur quels en-têtes de la bibliothèque C++ standard incluent quels autres en-têtes de la bibliothèque C++ standard. Cela rend le code portable entre les versions et les plateformes. Au moins deux changements d’en-tête dans Visual Studio 2015 affectent le code utilisateur. Tout d’abord, \<string> n’inclut plus \<iterator>. Deuxièmement, \<tuple> déclare à présent `std::array` sans inclure tous les \<array>, ce qui peut casser le code par la combinaison suivante de constructions de code : votre code a une variable nommée « array », vous avez une directive using « using namespace std; » et vous incluez un en-tête de la bibliothèque C++ standard (tel que \<functional>) qui inclut \<tuple>, qui déclare maintenant `std::array`.

- **steady_clock**

   L’implémentation \<chrono> de [steady_clock](../standard-library/steady-clock-struct.md) a changé pour satisfaire les exigences de la norme C++ en matière de stabilité et d’unitonicité. `steady_clock` est maintenant basé sur [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx), et `high_resolution_clock` est désormais un typedef pour `steady_clock`. Ainsi, dans Visual Studio, `steady_clock::time_point` est désormais un typedef pour `chrono::time_point<steady_clock>`. Toutefois, cela n’est pas nécessairement le cas pour d’autres implémentations.

- **allocateurs et const**

   Nous avons à présent besoin de comparaisons d'égalité/inégalité d'allocateurs pour accepter des arguments const des deux côtés. Si vos allocateurs définissent ces opérateurs comme ceci,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   vous devez les mettre à jour et les déclarer en tant que membres const :

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **Éléments const**

   La norme C++ a toujours interdit les conteneurs d’éléments const (tels que vector\<const T> ou set\<const T>). Visual Studio 2013 et les versions antérieures acceptaient ces conteneurs. Dans la version actuelle, la compilation de ces conteneurs échoue.

- **std::allocator::deallocate**

   Dans Visual Studio 2013 et versions antérieures, `std::allocator::deallocate(p, n)` ignorait l’argument passé pour *n*.  La norme C++ a toujours nécessité que *n* soit égal à la valeur passée comme premier argument à l’appel de `allocate` qui retournait *p*. Toutefois, dans la version actuelle, la valeur de *n* est inspectée. Un code qui passe des arguments pour *n* non conformes à la norme peut échouer au moment de l’exécution.

- **hash_map et hash_set**

   Les fichiers d’en-tête non standard \<hash_map> et \<hash_set> sont dépréciés dans Visual Studio 2015 et seront supprimés dans une version ultérieure. Utilisez \<unordered_map> et \<unordered_set> à la place.

- **comparateurs et operator()**

   Les conteneurs associatifs (famille \<map>) exigent que leurs comparateurs possèdent des opérateurs d’appel de fonction pouvant être appelée par const. À présent, la compilation du code suivant dans une déclaration de classe de comparateur échoue :

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Pour résoudre cette erreur, remplacez la déclaration de fonction par :

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **caractéristiques de type**

   Les anciens noms des caractéristiques de type issues d'une version antérieure du projet de norme C++ ont été supprimés. Ils ont été modifiés dans C++11 et ont été mis à jour selon les valeurs C++11 dans Visual Studio 2015. Le tableau ci-dessous répertorie les anciens noms et les nouveaux.

   |Ancien nom|Nouveau nom|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **stratégies launch::any et launch::sync**

   Les stratégies non standard `launch::any` et `launch::sync` ont été supprimées. Pour `launch::any`, utilisez `launch:async | launch:deferred` à la place. Pour `launch::sync`, utilisez `launch::deferred`. Consultez [launch, énumération](../standard-library/future-enums.md#launch).

####  <a name="BK_MFC"></a> MFC et ATL

- **Microsoft Foundation Classes (MFC)**

   n’est plus inclus dans une installation « Par défaut » de Visual Studio en raison de sa grande taille. Pour installer MFC, choisissez l’option d’installation **Personnalisée** dans le programme d’installation de Visual Studio 2015. Si vous avez déjà installé Visual Studio 2015, vous pouvez installer MFC en réexécutant le programme d’installation de **Visual Studio**. Choisissez l’option d’installation **Personnalisée**, puis choisissez **Microsoft Foundation Classes**. Vous pouvez exécuter le programme d’installation de **Visual Studio** à partir de **Programmes et fonctionnalités** dans le **Panneau de configuration**, ou à partir du support d’installation.

   Le package redistribuable Visual C++ inclut toujours cette bibliothèque.

####  <a name="BK_ConcRT"></a> Runtime d’accès concurrentiel

- **Macro Yield de Windows.h en conflit avec concurrency::Context::Yield**

   Le runtime d’accès concurrentiel utilisait précédemment `#undef` pour annuler la définition de la macro Yield afin d’éviter les conflits entre la macro Yield définie dans Windows.h et la fonction `concurrency::Context::Yield`. Ce `#undef` a été supprimé, et un nouvel appel d’API équivalent non conflictuel, [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution), a été ajouté. Pour contourner les conflits avec Yield, vous pouvez mettre à jour votre code afin d’appeler à la place la fonction `YieldExecution` ou bien mettre entre parenthèses le nom de la fonction `Yield` sur les sites d’appel, comme dans l’exemple suivant :

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Améliorations de la conformité du compilateur dans Visual Studio 2015

Pendant la mise à niveau du code de versions précédentes, vous pouvez également rencontrer des erreurs de compilateur dues à des améliorations de la conformité dans Visual Studio 2015. Ces améliorations n’interrompent pas la compatibilité binaire des versions antérieures de Visual Studio, mais peuvent produire des erreurs de compilateur qui n’existaient pas auparavant. Pour plus d’informations, consultez [Nouveautés de Visual C++ entre 2003 et 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

Dans Visual Studio 2015, les améliorations suivies de la conformité du compilateur peuvent parfois modifier la façon dont le compilateur comprend votre code source existant. En conséquence, vous pouvez être confronté à des erreurs nouvelles ou différentes pendant la génération, ou même à des différences de comportement dans le code qui auparavant était généré et paraissait s’exécuter correctement.

Heureusement, ces différences n’ont que peu ou pas d’impact sur la plupart de votre code source. Quand un changement du code source ou autre est nécessaire pour résoudre ces différences, les corrections ont tendance à être petites et simples. Nous avons inclus de nombreux exemples de code source précédemment acceptable qui devront peut-être être changés *(avant)* et les corrections pour les modifier *(après)*.

Même si ces différences peuvent affecter votre code source ou d’autres artefacts de build, elles n’affectent pas la compatibilité binaire entre les mises à jour des versions de Visual Studio. Un *changement cassant* est plus sérieux et peut affecter la compatibilité binaire, mais ces types d’incompatibilités binaires se produisent uniquement entre les versions principales de Visual Studio, par exemple entre Visual Studio 2013 et Visual Studio 2015. Pour plus d’informations sur les modifications avec rupture qui se sont produites entre Visual Studio 2013 et Visual Studio 2015, consultez [Modifications de la mise en conformité de Visual Studio 2015](#VC_2015).

- [Améliorations de la conformité dans Visual Studio 2015](#VS_RTM)

- [Améliorations de la conformité dans Update 1](#VS_Update1)

- [Améliorations de la conformité dans Update 2](#VS_Update2)

- [Améliorations de la conformité dans Update 3](#VS_Update3)

###  <a name="VS_RTM"></a> Améliorations de la conformité dans Visual Studio 2015

- /Zc:forScope-

   L’option de compilateur `/Zc:forScope-` est dépréciée. Elle sera supprimée dans une version ultérieure.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   En général, cette option était utilisée pour autoriser du code non standard utilisant des variables de boucle après le point où, selon la norme, elles devraient être hors de portée. Elle était nécessaire uniquement quand vous compiliez avec l’option `/Za`, car sans `/Za`, l’utilisation d’une variable de boucle for après la fin de la boucle est toujours autorisée. Si vous ne vous souciez pas de la conformité aux normes (par exemple, si le code n’est pas destiné à d’autres compilateurs), vous pouvez éventuellement désactiver l’option `/Za` (ou assigner à la propriété **Désactivation des extensions de langage** la valeur **Non**). Si vous souhaitez écrire un code portable, conforme aux normes, vous devez réécrire votre code afin qu'il soit conforme à la norme en déplaçant la déclaration de ces variables vers un point extérieur à la boucle.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- Option de compilateur `/Zg`

   L’option de compilateur `/Zg` (Générer des prototypes de fonction) n’est plus disponible. Cette option de compilateur a été déconseillée précédemment.

- Vous ne pouvez plus exécuter de tests unitaires avec C++/CLI à partir de la ligne de commande avec mstest.exe. À la place, utilisez vstest.console.exe. Consultez [Options de ligne de commande VSTest.Console.exe](/visualstudio/test/vstest-console-options).

- **Mot clé mutable**

   Le spécificateur de classe de stockage **mutable** n’est plus autorisé dans les emplacements où il était compilé sans erreur. À présent, le compilateur attribue l'erreur C2071 (classe de stockage non conforme). Conformément à la norme, le spécificateur **mutable** peut être appliqué uniquement à des noms de données membres de classe. Il ne peut pas être appliqué à des noms déclarés const ou static, ni à des membres de référence.

   Considérons par exemple le code suivant :

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Les versions précédentes du compilateur acceptaient cela, mais le compilateur attribue désormais l’erreur suivante :

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Pour corriger l’erreur, supprimez le mot clé **mutable** redondant.

- **char_16_t et char32_t**

   Vous ne pouvez plus utiliser `char16_t` ou `char32_t` comme alias dans un **typedef**, car ces types sont maintenant traités comme des types intégrés. Les utilisateurs et les auteurs de bibliothèques définissaient souvent `char16_t` et `char32_t` comme alias de `uint16_t` et `uint32_t`, respectivement.

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   Pour mettre à jour le code, supprimez les déclarations **typedef** et renommez tous les autres identificateurs qui entrent en conflit avec ces noms.

- **Paramètres de modèle sans type**

   Du code qui implique des paramètres de modèle sans type fait à présent l'objet d'une vérification correcte de la compatibilité des types quand vous fournissez des arguments template explicites. Par exemple, le code suivant pouvait être compilé sans erreur dans les versions antérieures de Visual Studio.

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   Le compilateur actuel attribue normalement une erreur, car le type de paramètre de modèle ne correspond pas à l'argument template (le paramètre est un pointeur vers un membre const, mais la fonction f est non const) :

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Pour résoudre cette erreur dans votre code, assurez-vous que le type de l’argument template que vous utilisez correspond au type déclaré du paramètre de modèle.

- **__declspec(align)**

   Le compilateur n'accepte plus `__declspec(align)` sur les fonctions. Cette construction était toujours ignorée, mais à présent elle génère une erreur du compilateur.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Pour résoudre ce problème, supprimez `__declspec(align)` de la déclaration de fonction. Comme cela n’avait aucun effet, la suppression ne change rien.

- **Gestion des exceptions**

   Quelques modifications ont été apportées à la gestion des exceptions. Tout d'abord, les objets d'exception doivent pouvoir être copiés ou déplacés. Le code suivant se compile dans Visual Studio 2013, mais pas dans Visual Studio 2015 :

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Le problème est que le constructeur de copie est privé, si bien que l’objet ne peut pas être copié comme dans le cours normal de la gestion d’une exception. Il en va de même quand le constructeur de copie est déclaré **explicit**.

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Pour mettre à jour votre code, vérifiez que le constructeur de copie de l’objet d’exception est **public** et qu’il n’est pas marqué **explicit**.

   L'interception d'une exception par sa valeur exige que l'objet d'exception puisse être copié. Le code suivant se compile dans Visual Studio 2013, mais pas dans Visual Studio 2015 :

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   Vous pouvez résoudre ce problème en remplaçant le type de paramètre de **catch** par une référence.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Littéraux de chaîne suivis par des macros**

   Le compilateur prend désormais en charge les littéraux définis par l’utilisateur. Par conséquent, les littéraux de chaîne suivis par des macros sans espace blanc intermédiaire sont interprétés comme des littéraux définis par l'utilisateur, qui peuvent entraîner des erreurs ou des résultats inattendus. Par exemple, dans les compilateurs précédents, le code suivant pouvait être compilé avec succès :

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   Le compilateur interprétait ce code comme un littéral de chaîne « hello » suivi par une macro, correspondant à « there » étendu, puis les deux littéraux de chaîne étaient concaténés en un seul. Dans Visual Studio 2015, le compilateur interprète cette séquence comme un littéral défini par l’utilisateur, mais comme il n’existe aucun littéral `_x` correspondant défini par l’utilisateur, une erreur est générée.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Pour résoudre ce problème, ajoutez un espace entre le littéral de chaîne et la macro.

- **Littéraux de chaîne adjacents**

   Comme précédemment, en raison des modifications associées dans l'analyse des chaînes, les littéraux de chaîne adjacents (littéraux de chaîne aux caractères larges ou étroits) sans espace blanc étaient interprétés comme une chaîne concaténée unique dans les versions antérieures de Visual C++. Dans Visual Studio 2015, vous devez maintenant ajouter un espace blanc entre les deux chaînes. Par exemple, le code suivant doit être modifié :

    ```cpp
    char * str = "abc""def";
    ```

   Pour résoudre ce problème, ajoutez un espace entre les deux chaînes :

    ```cpp
    char * str = "abc" "def";
    ```

- **Placement new et delete**

   Une modification a été apportée à l’opérateur **delete** pour le rendre conforme à la norme C++14. Vous trouverez les détails relatifs au changement de normes sur la page décrivant la [libération dimensionnée C++](http://isocpp.org/files/papers/n3778.html). Les changements ajoutent une forme de l’opérateur **delete** global, qui accepte un paramètre de taille. Il s’agit d’un changement cassant pour la raison suivante : si vous utilisiez un opérateur **delete** avec la même signature (pour correspondre à un opérateur **placement new**), vous recevez une erreur de compilation C2956 (qui se produit au point où l’opérateur placement new est utilisé, car il s’agit de la position dans le code où le compilateur tente d’identifier l’opérateur **delete** correspondant approprié).

   La fonction `void operator delete(void *, size_t)` était un opérateur **placement delete** correspondant à la fonction **placement new** `void * operator new(size_t, size_t)` dans C++11. Avec la libération dimensionnée C++14, cette fonction delete est maintenant une *fonction de libération habituelle* (opérateur **delete** global). La norme impose que si l'utilisation d'un opérateur placement new recherche une fonction delete correspondante et trouve une fonction de désallocation habituelle, le programme est incorrect.

   Par exemple, votre code définit à la fois un opérateur **placement new** et un opérateur **placement delete** :

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   Le problème se produit en raison de la correspondance dans les signatures de fonction entre un opérateur **placement delete** que vous avez défini et le nouvel opérateur **delete** dimensionné global. Déterminez si vous pouvez utiliser un autre type que `size_t` pour les opérateurs **placement new** et **delete**. Le type du **typedef** `size_t` dépend du compilateur. Il s’agit d’un **typedef** pour **unsigned int** dans MSVC. Nous vous recommandons d’utiliser un type énuméré tel que celui-ci :

    ```cpp
    enum class my_type : size_t {};
    ```

   Changez ensuite votre définition de **placement new** et **delete** pour utiliser ce type comme deuxième argument à la place de `size_t`. Vous devez également mettre à jour les appels à placement new pour passer le nouveau type (par exemple, en utilisant `static_cast<my_type>` pour effectuer une conversion à partir de la valeur entière) et mettre à jour la définition de **new** et **delete** pour recaster vers le type entier. Vous n’avez pas besoin d’utiliser un **enum** pour cela. Un type de classe avec un membre `size_t` fonctionne également.

   Une autre solution consiste à éliminer complètement **placement new**. Si votre code utilise **placement new** pour implémenter un pool de mémoires où l’argument de positionnement correspond à la taille de l’objet alloué ou supprimé, la fonction de libération dimensionnée peut servir à remplacer votre propre code de pool de mémoires personnalisé. De plus, vous pouvez supprimer les fonctions de positionnement et les remplacer simplement par un opérateur **delete** à deux arguments.

   Si vous ne voulez pas mettre à jour votre code tout de suite, vous pouvez revenir à l’ancien comportement en utilisant l’option de compilateur `/Zc:sizedDealloc-`. Si vous utilisez cette option, il n’y a pas de conflit avec votre opérateur **placement delete** puisque les fonctions delete à deux arguments n’existent pas.

- **Membres de données d’union**

   Les membres de données d'unions ne peuvent plus posséder de types de référence. Le code suivant se compile correctement dans Visual Studio 2013, mais génère une erreur dans Visual Studio 2015.

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   Le code précédent génère les erreurs suivantes :

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Pour résoudre ce problème, modifiez les types de référence en spécifiant un pointeur ou une valeur. La modification du type en pointeur nécessite des modifications dans le code qui utilise le champ union. La modification du code en valeur modifierait les données stockées dans l'union, ce qui affecte les autres champs dans la mesure où les champs dans les types d'union partagent la même mémoire. Selon la taille de la valeur, cela peut également modifier la taille de l'union.

- Les unions anonymes sont à présent plus conformes à la norme. Les versions précédentes du compilateur généraient un constructeur explicite et un destructeur pour les unions anonymes. Ces fonctions générées par le compilateur sont supprimées dans Visual Studio 2015.

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   Le code précédent génère l’erreur suivante dans Visual Studio 2015 :

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Pour résoudre ce problème, fournissez vos propres définitions du constructeur et/ou du destructeur.

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **Unions avec structs anonymes**

   Pour se conformer à la norme, le comportement d'exécution a changé pour les membres de structures anonymes dans les unions. Le constructeur pour les membres de structure anonymes dans une union n'est plus implicitement appelé lors de la création d'une telle union. De plus, le destructeur pour les membres de structure anonymes dans une union n'est plus implicitement appelé quand l'union passe hors de portée. Considérons le code suivant, dans lequel une union U contient une structure anonyme contenant un membre de structure nommé S possédant un destructeur.

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Dans Visual Studio 2013, le constructeur de S est appelé quand l’union est créée, et le destructeur de S est appelé quand la pile de la fonction f est nettoyée. Mais dans Visual Studio 2015, le constructeur et le destructeur ne sont pas appelés. Le compilateur émet un avertissement à propos de ce changement de comportement.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Pour restaurer le comportement d'origine, nommez la structure anonyme. Le comportement d'exécution des structures non anonymes est le même, quelle que soit la version du compilateur.

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Sinon, essayez de déplacer le code du constructeur et du destructeur dans de nouvelles fonctions et ajoutez des appels à ces fonctions à partir du constructeur et du destructeur pour l'union.

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **Résolution de modèle**

   Des modifications ont été apportées à la résolution de noms pour les modèles. En C++, quand vous envisagez des candidats pour la résolution d'un nom, il peut arriver qu'un ou plusieurs noms considérés comme des correspondances potentielles produisent une instanciation de modèle non valide. Ces instanciations non valides ne provoquent normalement pas d’erreurs du compilateur, un principe appelé SFINAE (Substitution Failure Is Not An Error).

   À présent, si le principe SFINAE exige que le compilateur instancie la spécialisation d'un modèle de classe, toutes les erreurs qui surviennent au cours de ce processus sont des erreurs du compilateur. Dans les versions précédentes, le compilateur ignore de telles erreurs. Considérons par exemple le code suivant :

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   Si vous effectuez une compilation avec le compilateur actuel, vous obtenez l'erreur suivante :

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   La raison en est qu’au point de la première invocation de is_base_of, la classe `D` n’a pas encore été définie.

   Dans ce cas, la correction proposée consiste à ne pas utiliser de tels traits de type tant que la classe n’a pas été définie. Si vous déplacez les définitions de `B` et `D` au début du fichier de code, l’erreur est résolue. Si les définitions sont dans des fichiers d'en-tête, vérifiez l'ordre des instructions include pour les fichiers d'en-tête afin de vous assurer que toutes les définitions de classe sont compilées avant l'utilisation des modèles problématiques.

- **Constructeurs de copie**

   Dans Visual Studio 2013 et Visual Studio 2015, le compilateur génère un constructeur de copie pour une classe, si celle-ci a un constructeur de déplacement défini par l’utilisateur mais aucun constructeur de copie personnalisé. Dans Dev14, ce constructeur de copie généré implicitement est également marqué « = delete ».

<!--From here to VS_Update1 added 04/21/2017-->

- **main déclaré comme 'C' externe nécessite désormais un type de retour.**

   Le code suivant génère désormais l’erreur C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Pour corriger cette erreur, ajoutez le type de retour :

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **typename n’est pas autorisé dans un initialiseur de membre**

   Le code suivant génère désormais l’erreur C2059 :

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   Pour corriger cette erreur, supprimez `typename` de l’initialiseur :

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **La classe de stockage sur les spécialisations explicites est ignorée.**

   Dans le code suivant, le spécificateur de classe de stockage static est ignoré

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **Une constante utilisée dans static_assert à l’intérieur d’un modèle de classe échoue systématiquement.**

   Le code suivant provoque l’échec systématique de `static_assert` :

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Pour contourner ce problème, incluez la valeur dans un wrapper dans un **struct** :

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **Règles appliquées pour les prédéclarations. (S’applique uniquement à C.)**

   Le code suivant génère désormais l’erreur C2065 :

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Pour corriger ce problème, ajoutez les prédéclarations appropriées :

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Mise en application plus cohérente des types de pointeurs de fonction**

   Le code suivant génère désormais l’erreur C2197 :

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Appels ambigus à des fonctions surchargées**

   Le code suivant génère désormais l’erreur C266 : 'N::bind' : appel ambigu à une fonction surchargée

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   Pour corriger cette erreur, utilisez un nom qualifié complet d’appel à `bind: N::bind(...)`. Toutefois, si cette modification est manifeste via un identificateur non déclaré (C2065), il peut être judicieux de résoudre ce problème en utilisant une déclaration **using** à la place.

   Cela se produit fréquemment avec ComPtr et d’autres types dans l’espace de noms `Microsoft::WRL`.

- **Résoudre une adresse incorrecte de**

   Le code suivant génère désormais l’erreur C2440 : '=' : impossible de convertir 'type *' en 'type'. Pour corriger cette erreur, remplacez &(type) par (type) et (&f()) par (f()).

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **Le littéral de chaîne est un tableau de constantes**

   Le code suivant génère désormais l’erreur C2664 : 'void f(void *)' : impossible de convertir l’argument 1 de 'const char (*)[2]' en 'void *'

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Pour corriger cette erreur, remplacez le type de paramètre de fonction par `const void*`, ou modifiez le corps de `h` pour qu’il ressemble à cet exemple :

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **Chaînes UDL C++11**

   Le code suivant génère désormais l’erreur C3688 : suffixe littéral non valide 'L' ; opérateur littéral ou modèle d’opérateur littéral 'operator ""L' introuvable

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Pour corriger cette erreur, modifiez le code pour ajouter un espace :

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Dans l’exemple ci-dessus, `MACRO` n’est plus analysé comme deux jetons (une chaîne suivie d’une macro). Maintenant, il est analysé comme un UDL de jeton unique. Il en va de même pour L""L"" qui était auparavant analysé comme L"" et L"", et qui est maintenant analysé comme L""L et "".

   Les règles de concaténation de chaîne ont également été mises en conformité avec la norme, ce qui signifie que L"a" "b" est équivalent à L"ab". Les éditions précédentes de Visual Studio n’acceptaient pas la concaténation de chaînes avec une largeur des caractères différente.

- **Caractère vide C++11 supprimé**

   Le code suivant génère désormais l’erreur C2137 : constante caractère vide

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Pour corriger cette erreur, modifiez le code pour rendre la valeur Null explicite :

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Les exceptions MFC ne peuvent pas être interceptées par valeur, car elles ne peuvent pas être copiées**

   Le code suivant dans une application MFC génère maintenant l’erreur C2316 : 'D': ne peut pas être intercepté en tant que destructeur et/ou le constructeur de copie est inaccessible ou supprimé

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   Pour corriger le code, vous pouvez remplacer le bloc catch par `catch (const D &)`, mais la meilleure solution consiste généralement à utiliser les macros MFC TRY/CATCH.

- **alignof est désormais un mot clé**

   Le code suivant génère désormais l’erreur C2332 : 'classe' : nom de balise manquant. Pour corriger le code, vous devez renommer la classe ou, si la classe effectue le même travail qu’**alignof**, remplacer simplement la classe par le nouveau mot clé.

    ```cpp
    class alignof{}
    ```

- **constexpr est désormais un mot clé**

   Le code suivant génère désormais l’erreur C2059 : erreur de syntaxe : ')'. Pour corriger le code, vous devez renommer toute fonction ou variable qui est appelée « constexpr ».

    ```cpp
    int constexpr() {return 1;}
    ```

- **Les types déplaçables ne peuvent pas être const**

   Quand une fonction retourne un type qui est destiné à être déplacé, son type de retour ne doit pas être **const**.

- **Constructeurs de copie supprimés**

   Le code suivant génère désormais l’erreur C2280, 'S::S(S &&)' : tentative de référencement d’une fonction supprimée :

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Pour corriger cette erreur, utilisez une initialisation directe pour `S2` :

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Conversion en pointeur de fonction générée uniquement en l’absence de capture lambda**

   Le code suivant génère l’erreur C2664 dans Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Pour corriger cette erreur, supprimez `=` de la liste de capture.

- **Appels ambigus impliquant des opérateurs de conversion**

   Le code suivant génère désormais l’erreur C2440 : 'cast de type' : impossible de convertir 'S2' en 'S1' :

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   Pour corriger cette erreur, appelez explicitement l’opérateur de conversion :

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Le code suivant génère désormais l’erreur C2593 : 'operator =' est ambigu :

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   Pour corriger cette erreur, appelez explicitement l’opérateur de conversion :

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Corriger l’initialisation de copie non valide dans l’initialisation de données membres non static (NSDMI)**

   Le code suivant génère désormais l’erreur C2664 : 'S1::S1(S1 &&)' : impossible de convertir l’argument 1 de 'bool' en 'const S1 &' :

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Pour corriger cette erreur, utilisez une initialisation directe :

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Accès aux constructeurs dans les instructions decltype**

   Le code suivant génère désormais l’erreur C2248 : 'S::S' : ne peut pas accéder à un membre privé déclaré dans la classe 'S' :

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   Corrigez cette erreur en ajoutant une déclaration friend pour `S2` dans `S` :

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Le constructeur par défaut de l’expression lambda est implicitement supprimé**

   Le code suivant génère désormais l’erreur C3497 : vous ne pouvez pas construire une instance d’expression lambda :

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Pour corriger cette erreur, supprimez le besoin d’appeler le constructeur par défaut. Si l’expression lambda ne capture rien, elle peut être convertie en pointeur de fonction.

- **Expressions lambda avec un opérateur d’assignation supprimé**

   Le code suivant génère désormais l’erreur C2280 :

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   Pour corriger cette erreur, remplacez l’expression lambda par une classe foncteur ou supprimez le besoin d’utiliser l’opérateur d’assignation.

- **Tentative de déplacement d’un objet avec un constructeur de copie supprimé**

   Le code suivant génère désormais l’erreur C2280 : 'moveable::moveable(const moveable &)' : tentative de référencement d’une fonction supprimée

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   Pour corriger cette erreur, utilisez `std::move` à la place :

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **La classe locale ne peut pas référencer une autre classe locale définie plus loin dans la même fonction**

   Le code suivant génère désormais l’erreur C2079 : 's' utilise le struct non défini 'main::S2'

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   Pour corriger cette erreur, placez la définition de `S2` plus haut dans le code :

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **Impossible d’appeler un constructeur de base protégé dans le corps du constructeur dérivé.**

   Le code suivant génère désormais l’erreur C2248 : 'S1::S1' : ne peut pas accéder à un membre protégé déclaré dans la classe 'S1'

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   Pour corriger cette erreur, supprimez dans `S2` l’appel de `S1()` à partir du constructeur et placez-le si nécessaire dans une autre fonction.

- **{} empêche la conversion en pointeur**

   Le code suivant génère désormais l’erreur C2439 : 'S::p' : impossible d’initialiser le membre

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Pour corriger cette erreur, supprimez les accolades autour du `0` ou bien utilisez **nullptr** à la place, comme indiqué dans cet exemple :

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Définition de macro incorrecte et utilisation de parenthèses**

   L’exemple suivant génère désormais l’erreur C2008 : ';' : inattendu dans la définition d’une macro

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Pour corriger le problème, remplacez la ligne supérieure par `#define A();`

   Le code suivant génère l’erreur C2059 : erreur de syntaxe : ')'

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Pour corriger le code, supprimez l’espace entre A et ().

   Le code suivant génère l’erreur C2091 : fonction retournée par la fonction :

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Pour corriger cette erreur, supprimez les parenthèses après DECLARE dans S : `DECLARE;`.

   Le code suivant génère l’erreur C2062 : type 'int' inattendu

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Pour corriger le problème, définissez `A` comme suit :

    ```cpp
    #define A int
    ```

- **Parenthèses supplémentaires dans les déclarations**

   Le code suivant génère l’erreur C2062 : type 'int' inattendu

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Pour corriger cette erreur, supprimez les parenthèses autour de `j`. Si les parenthèses sont nécessaires pour plus de clarté, utilisez un **typedef**.

- **Constructeurs générés par le compilateur et __declspec(novtable)**

   Dans Visual Studio 2015, il existe un risque accru que les constructeurs inline générés par le compilateur des classes abstraites avec des classes de base virtuelles exposent une utilisation incorrecte de `__declspec(novtable)` quand il est utilisé avec `__declspec(dllimport)`.

- **auto nécessite une seule expression dans une initialisation de liste directe**

   Le code suivant génère maintenant l’erreur C3518 : 'testPositions'. Dans un contexte d’initialisation de liste directe, le type pour 'auto' peut uniquement être déduit à partir d’une seule expression d’initialiseur

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Pour corriger cette erreur, une possibilité consiste à initialiser `testPositions` comme suit :

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Vérification des types et des pointeurs vers des types pour is_convertible**

   Le code suivant provoque désormais l’échec de l’assertion statique.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Pour corriger cette erreur, modifiez `static_assert` afin de comparer les pointeurs à `D` et `B2` :

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **Les déclarations __declspec(novtable) doivent être cohérentes**

   Les déclarations `__declspec` doivent être cohérentes entre toutes les bibliothèques. Le code suivant génère désormais une violation à une règle de définitions (ODR) :

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

###  <a name="VS_Update1"></a> Améliorations de la conformité dans Update 1

- **Classes de base virtuelles privées et héritage indirect**

   Les versions précédentes du compilateur autorisaient une classe dérivée à appeler des fonctions membres de ses classes de base `private virtual` dérivées indirectement. Cet ancien comportement était incorrect et non conforme à la norme C++. Le compilateur n’accepte plus de code écrit de cette façon. Il émet dans ce cas l’erreur du compilateur C2280.

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   Exemple (avant)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   Exemple (après)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \- ou -

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Opérateurs new et delete surchargés**

   Avec les versions précédentes du compilateur, vous pouviez déclarer un **operator new** non membre et un **operator delete** non membre comme static, et vous pouviez les déclarer dans d’autres espaces de noms que l’espace de noms global.  Cet ancien comportement présentait un risque. En effet, il pouvait arriver que le programme n’appelle pas l’implémentation de l’opérateur **new** ou **delete** prévue par le programmeur, ce qui entraînait un comportement d’exécution incorrect sans générer d’avertissement. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C2323.

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   Exemple (avant)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   Exemple (après)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   De plus, bien que le compilateur ne donne pas de diagnostic spécifique, l’opérateur **new** inline est considéré comme incorrect.

- **Appel de 'operator *type*()' (conversion définie par l’utilisateur) sur des types autres que des types classe**

   Les versions précédentes du compilateur autorisaient l’appel de ’operator *type*()’ sur des types autres que des types classe et ignoraient cet appel en silence. Cet ancien comportement créait un risque de génération de code incorrect en mode silencieux qui provoquait un comportement imprévisible au moment de l’exécution. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C2228.

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   Exemple (avant)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   Exemple (après)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **Typename redondant dans les spécificateurs de type élaborés**

   Les versions précédentes du compilateur autorisaient l’utilisation de **typename** dans les spécificateurs de type élaborés, mais le code écrit de cette manière est sémantiquement incorrect. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C3406.

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   Exemple (avant)

    ```cpp
    template <typename class T>
    class container;
    ```

   Exemple (après)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **Déduction de type des tableaux à partir d’une liste d’initialiseurs**

   Les versions précédentes du compilateur ne prenaient pas en charge la déduction de type des tableaux à partir d’une liste d’initialiseurs. Le compilateur prend désormais en charge cette forme de déduction de type. Ainsi, les appels à des modèles de fonctions à l’aide de listes d’initialiseurs peuvent maintenant être ambigus ou une surcharge autre que dans les versions précédentes du compilateur peut être choisie. Pour résoudre ces problèmes, le programme doit maintenant spécifier explicitement la surcharge prévue par le programmeur.

   Quand, à cause de ce nouveau comportement, la résolution de surcharge prend en compte un candidat supplémentaire qui est tout aussi efficace que le candidat historique, l’appel devient ambigu et le compilateur émet l’erreur C2668.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Exemple 1 : appel ambigu à une fonction surchargée (avant)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   Exemple 1 : appel ambigu à une fonction surchargée (après)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   Quand, à cause de ce nouveau comportement, la résolution de surcharge prend en compte un candidat supplémentaire qui est une meilleure correspondance que le candidat historique, l’appel résout sans ambiguïté le nouveau candidat, ce qui provoque une modification du comportement du programme probablement différente de ce que le programmeur a prévu.

   Exemple 2 : modification de la résolution de surcharge (avant)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   Exemple 2 : modification de la résolution de surcharge (après)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **Restauration des avertissements d’instruction switch**

   Une version précédente du compilateur supprimait certains avertissements liés aux instructions **switch**. Ces avertissements ont été rétablis. Le compilateur émet désormais les avertissements restaurés, et les avertissements liés à des cas spécifiques (notamment le cas par défaut) sont désormais émis sur la ligne contenant le cas qui pose problème, plutôt que sur la dernière ligne de l’instruction switch. Comme ces avertissements ne sont plus émis sur les mêmes lignes qu’auparavant, les avertissements précédemment supprimés à l’aide de `#pragma warning(disable:####)` peuvent ne plus être supprimés comme prévu. Pour supprimer ces avertissements comme prévu, vous devrez peut-être déplacer la directive `#pragma warning(disable:####)` vers une ligne au-dessus du premier cas incriminé. Voici les avertissements restaurés :

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   Exemple d’avertissement C4063 (avant)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   Exemple d’avertissement C4063 (après)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   Des exemples des autres avertissements restaurés sont fournis dans leur documentation.

- **#include : utilisation du spécificateur de répertoire parent '..' dans le chemin** (concerne uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas l’utilisation du spécificateur de répertoire parent ’..’ dans le chemin des directives `#include`. Le code écrit de cette manière est généralement conçu pour inclure des en-têtes qui existent en dehors du projet en utilisant de manière incorrecte des chemins d’accès relatifs au projet. Cet ancien comportement créait un risque que le programme puisse être compilé en incluant un fichier source différent de celui prévu par le programmeur, ou que ces chemins d’accès relatifs ne soient pas portables vers d’autres environnements de génération. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C4464 facultatif si cette fonctionnalité est activée.

    ```Output
    warning C4464: relative include path contains '..'
    ```

   Exemple (avant)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   Exemple (après)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   De plus, bien que le compilateur ne donne pas de diagnostic spécifique, nous vous recommandons également de ne pas utiliser le spécificateur de répertoire parent « .. » pour spécifier les répertoires Include de votre projet.

- **#pragma optimize() s’étend au-delà de la fin du fichier d’en-tête** (affecte uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas les modifications apportées aux paramètres de l’indicateur d’optimisation qui échappent un fichier d’en-tête inclus dans une unité de traduction. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C4426 facultatif à l’emplacement du `#include`incriminé, si cette fonctionnalité est activée. Cet avertissement est émis uniquement si le modifications entrent en conflit avec les indicateurs d’optimisation définis par des arguments de ligne de commande au compilateur.

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   Exemple (avant)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   Exemple (après)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **Incompatibilité de #pragma warning(push)** et de **#pragma warning(pop)** (affecte uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas les associations des modifications d’état `#pragma warning(push)` aux modifications d’état `#pragma warning(pop)` dans un autre fichier source, qui sont rarement souhaitées. Cet ancien comportement créait un risque que le programme soit compilé avec un autre ensemble d’avertissements activé que celui prévu par le programmeur, ce qui pouvait provoquer un comportement incorrect en mode silencieux. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C5031 facultatif à l’emplacement du `#pragma warning(pop)` correspondant, si cette fonctionnalité est activée. Cet avertissement inclut une note faisant référence à l’emplacement du #pragma warning(push) correspondant.

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   Exemple (avant)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   Exemple (après)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   Bien que rare, le code écrit de cette manière est parfois intentionnel. Le code écrit de cette manière est sensible aux modifications de l’ordre de `#include`. Dans la mesure du possible, nous conseillons que les fichiers de code source gèrent l’état d’avertissement de façon autonome.

- **#pragma warning(push) sans correspondance** (affecte uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur ne détectaient pas les modifications d’état `#pragma warning(push)` sans correspondance à la fin d’une unité de traduction. Désormais, le compilateur détecte le code écrit de cette façon et le notifie au programmeur. Il émet également un avertissement C5032 facultatif à l’emplacement du `#pragma warning(push)` sans correspondance, si cette fonctionnalité est activée. Cet avertissement est émis uniquement s’il n’y a aucune erreur de compilation dans l’unité de traduction.

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   Exemple (avant)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   Exemple (après)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **Des avertissements supplémentaires peuvent être émis à la suite du suivi d’état du #pragma warning amélioré**

   Les versions précédentes du compilateur ne suivaient pas les modifications de l’état d’avertissement #pragma assez bien pour émettre tous les avertissements prévus. Ce comportement créait un risque que certains avertissements soient supprimés dans des circonstances autres que celles prévues par le programmeur. Le compilateur effectue maintenant un suivi d’état de `#pragma warning` de manière plus complète, en particulier en ce qui concerne les changements d’état de `#pragma warning` dans les modèles. De plus, il émet éventuellement de nouveaux avertissements C5031 et C5032, destinés à aider le programmeur à détecter les utilisations involontaires de `#pragma warning(push)` et `#pragma warning(pop)`.

   Grâce à l’amélioration du suivi des changements d’état de `#pragma warning`, les avertissements qui étaient improprement supprimés ou ceux liés à des problèmes auparavant mal diagnostiqués peuvent désormais être émis.

- **Amélioration de l’identification du code inaccessible**

   Les modifications apportées à la bibliothèque standard C++ et la capacité améliorée à intégrer des appels de fonction par rapport aux versions précédentes du compilateur peuvent permettre au compilateur de prouver que du code est désormais inaccessible. Ce nouveau comportement peut provoquer des instances nouvelles et plus fréquentes de l’avertissement C4720.

    ```Output
    warning C4720: unreachable code
    ```

   Dans de nombreux cas, cet avertissement peut être émis uniquement lors de la compilation avec les optimisations activées, car les optimisations peuvent intégrer plus d’appels de fonction, supprimer le code redondant ou permettre de déterminer que du code est inaccessible. Nous avons constaté que de nouvelles instances de l’avertissement C4720 étaient fréquentes dans les blocs **try/catch**, en particulier en cas d’utilisation de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

   Exemple (avant)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   Exemple (après)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

###  <a name="VS_Update2"></a> Améliorations de la conformité dans Update 2

- **Des erreurs et avertissements supplémentaires peuvent être générés en raison de la prise en charge partielle de l’expression SFINAE.**

   Dans les versions précédentes du compilateur, certains types d’expressions au sein des spécificateurs **decltype** n’étaient pas analysés en raison de l’absence de prise en charge de l’expression SFINAE. Cet ancien comportement était incorrect et non conforme à la norme C++. À présent, le compilateur analyse ces expressions et offre une prise en charge partielle de l’expression SFINAE grâce à certaines améliorations récentes de la conformité. Par conséquent, le compilateur génère maintenant des avertissements et des erreurs détectés dans des expressions qui n’étaient pas analysées dans les versions précédentes du compilateur.

   Quand ce nouveau comportement analyse une expression **decltype** ayant un type qui n’a pas encore été déclaré, le compilateur génère l’erreur C2039.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Exemple 1 : utilisation d’un type non déclaré (avant)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   Exemple 1 (après)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   Quand ce nouveau comportement analyse une expression **decltype** dans laquelle il manque le mot clé **typename** obligatoire pour spécifier qu’un nom dépendant est un type, le compilateur génère l’avertissement C4346, ainsi que l’erreur C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Exemple 2 : le nom dépendant n’est pas un type (avant)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   Exemple 2 (après)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- Les variables membres `volatile`  **n’autorisent pas les constructeurs et les opérateurs d’assignation définis implicitement**

   Dans les versions précédentes du compilateur, il était possible de générer automatiquement les constructeurs de copie/déplacement par défaut et les opérateurs d’assignation de copie/déplacement par défaut pour une classe contenant des variables membres **volatiles**. Cet ancien comportement était incorrect et non conforme à la norme C++. À présent, le compilateur considère qu’une classe avec des variables membres **volatiles** a des opérateurs de construction et d’assignation non triviaux, ce qui empêche la génération automatique des implémentations par défaut de ces opérateurs. Quand une telle classe est membre d’une union (ou d’une union anonyme au sein d’une classe), les constructeurs de copie/déplacement et les opérateurs d’assignation de copie/déplacement de l’union (ou de la classe contenant l’union anonyme) sont implicitement définis comme étant supprimés. Toute tentative de construction ou de copie de l’union (ou de la classe contenant l’union anonyme) sans avoir défini explicitement les constructeurs ou opérateurs est considérée comme une erreur. Le compilateur génère alors l’erreur de compilateur C2280.

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   Exemple (avant)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   Exemple (après)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **Les fonctions membres statiques ne prennent pas en charge les qualificateurs cv.**

   Dans les versions précédentes de Visual Studio 2015, les fonctions membres statiques pouvaient contenir des qualificateurs cv. Ce comportement est dû à une régression effectuée dans Visual Studio 2015 et Visual Studio 2015 Update 1. Le code écrit de cette manière est refusé dans Visual Studio 2013 et les versions antérieures du compilateur. Le comportement de Visual Studio 2015 et Visual Studio 2015 Update 1 est incorrect, et n’est pas conforme à la norme C++.  Visual Studio 2015 Update 2 refuse le code écrit de cette façon et génère l’erreur de compilateur C2511.

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   Exemple (avant)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   Exemple (après)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **La déclaration anticipée d’enum n’est pas autorisée dans le code WinRT** (concerne uniquement `/ZW`)

   Le code compilé pour WinRT (Windows Runtime) ne prend pas en charge la déclaration anticipée des types **enum**, comme dans le cas de la compilation du code C++ managé pour .Net Framework à l’aide du commutateur de compilateur `/clr`. Ce comportement garantit que la taille d’une énumération est toujours connue et qu’elle peut être projetée correctement vers le système de type WinRT. Le compilateur refuse le code écrit de cette façon et génère l’erreur de compilateur C2599 ainsi que l’erreur de compilateur C3197.

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   Exemple (avant)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   Exemple (après)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **L’opérateur non membre surchargé new et l’opérateur delete ne peuvent pas être déclarés inline**. Le niveau 1 (`/W1`) est activé par défaut.

   Les versions précédentes du compilateur ne génèrent pas d’avertissement quand les fonctions d’opérateur non membre new et d’opérateur delete sont déclarées inline. Le code écrit de cette manière est incorrect (aucun diagnostic requis) et peut provoquer des problèmes de mémoire en raison de l’incompatibilité entre les opérateurs new et delete (en particulier, s’ils sont associés à la désallocation dimensionnée), qui peut être difficile à diagnostiquer. À présent, le compilateur génère l’avertissement C4595 pour faciliter l’identification du code écrit de cette manière.

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   Exemple (avant)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   Exemple (après)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   Pour corriger le code écrit de cette manière, vous devrez peut-être déplacer les définitions d’opérateur du fichier d’en-tête vers le fichier source correspondant.

###  <a name="VS_Update3"></a> Améliorations de la conformité dans Update 3

- **std::is_convertable détecte désormais l’auto-affectation** (bibliothèque standard)

   Les versions précédentes du trait de type `std::is_convertable` ne détectent pas correctement l’auto-affectation d’un type de classe quand son constructeur de copie est supprimé ou privé. Désormais, `std::is_convertable<>::value` a la valeur **false** (ce qui est correct) quand il est appliqué à un type de classe ayant un constructeur de copie supprimé ou privé.

   Aucun diagnostic du compilateur n’est associé à cette modification.

   Exemple

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   Dans les versions précédentes du compilateur, les assertions statiques en bas de cet exemple réussissent, car `std::is_convertable<>::value` a été incorrectement défini sur **true**. Désormais, `std::is_convertable<>::value` a la bonne valeur **false**, ce qui entraîne l’échec des assertions statiques.

- **Les constructeurs de copie et de déplacement ordinaires supprimés ou par défaut respectent les spécificateurs d’accès**

   Les versions précédentes du compilateur ne contrôlaient pas le spécificateur d’accès des constructeurs de copie et de déplacement ordinaires supprimés ou par défaut avant de les autoriser à être appelés. Cet ancien comportement était incorrect et non conforme à la norme C++. Dans certains cas, cet ancien comportement créait un risque de génération de code incorrect en mode silencieux qui provoquait un comportement imprévisible au moment de l’exécution. Le compilateur vérifie désormais le spécificateur d’accès des constructeurs de copie et de déplacement ordinaires supprimés ou par défaut pour déterminer s’ils peuvent être appelés et, dans le cas contraire, émet l’avertissement de compilateur C2248 en conséquence.

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   Exemple (avant)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   Exemple (après)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **Dépréciation de la prise en charge du code ATL avec attributs**. Le niveau 1 (`/W1`) est activé par défaut.

   Les versions précédentes du compilateur prenaient en charge le code ATL avec attributs. Comme phase suivante de la suppression de la prise en charge du code ATL avec attributs qui [est apparue dans Visual Studio 2008](https://msdn.microsoft.com/library/bb384632), le code ATL avec attributs a été déprécié. Le compilateur émet désormais l’avertissement C4467 pour faciliter l’identification de ce type de code déprécié.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Si vous souhaitez continuer à utiliser le code ATL avec attributs jusqu’à ce que la prise en charge soit supprimée du compilateur, vous pouvez désactiver cet avertissement en transmettant les arguments de ligne de commande `/Wv:18` ou `/wd:4467` au compilateur, ou en ajoutant `#pragma warning(disable:4467)` à votre code source.

   Exemple 1 (avant)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Exemple 1 (après)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Vous devez ou voulez parfois créer un fichier IDL pour éviter d’utiliser les attributs ATL dépréciés, comme dans l’exemple de code ci-dessous

   Exemple 2 (avant)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   Tout d’abord, créez le fichier *.idl ; le fichier vc140.idl généré peut être utilisé pour obtenir un fichier \*.idl contenant les interfaces et les annotations.

   Ajoutez ensuite une étape MIDL à votre génération pour vérifier que les définitions d’interface C++ sont générées.

   Exemple 2, IDL (après)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   Utilisez ensuite ATL directement dans le fichier d’implémentation, comme dans l’exemple de code ci-dessous.

   Exemple 2, implémentation (après)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **Fichiers d’en-tête précompilés (PCH) et directives #include incompatibles** (concerne uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur acceptaient les directives `#include` incompatibles dans les fichiers sources entre les compilations `-Yc` et `-Yu` lors de l’utilisation de fichiers d’en-tête précompilés (PCH). Le code écrit de cette façon n’est plus accepté par le compilateur.   Le compilateur émet désormais l’avertissement CC4598 pour faciliter l’identification des directives `#include` incompatibles lors de l’utilisation de fichiers PCH.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Exemple (avant) :

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Exemple (après)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Fichiers d’en-tête précompilés (PCH) et répertoires include incompatibles** (concerne uniquement `/Wall` `/WX`)

   Les versions précédentes du compilateur acceptaient les arguments de ligne de commande des répertoires Include `-I` incompatibles passés au compilateur entre les compilations `-Yc` et `-Yu` lors de l’utilisation de fichiers d’en-tête précompilés (PCH). Le code écrit de cette façon n’est plus accepté par le compilateur. Le compilateur émet désormais l’avertissement CC4599 pour faciliter l’identification des arguments de ligne de commande des répertoires Include (`-I`) incompatibles lors de l’utilisation de fichiers PCH.

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   Exemple (avant)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   Exemple (après)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Modifications de la mise en conformité de Visual Studio 2013

### <a name="compiler"></a>Compilateur

- Le mot clé **final** génère maintenant une erreur de symbole non résolu, alors que la compilation aurait auparavant réussi :

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   Dans les versions antérieures, aucune erreur n’était émise, car l’appel était un appel **virtuel**. Néanmoins, le programme échouait au moment de l’exécution. À présent, une erreur de l'éditeur de liens est émise car la classe est censée être finale. Dans cet exemple, pour corriger l'erreur, vous effectuez une liaison par rapport à l'objet qui contient la définition de `S2::f`.

- Quand vous utilisez des fonctions friend dans les espaces de noms, vous devez redéclarer la fonction friend avant de vous y référer ou vous obtiendrez une erreur, car le compilateur se conforme maintenant à la norme ISO C++. Par exemple, l’exemple suivant n’est plus compilé :

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   Pour corriger le code, déclarez la fonction **friend** :

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- La norme C++ n’autorise pas la spécialisation explicite dans une classe. Le compilateur Microsoft Visual C++ la permet dans certains cas, mais dans des cas tels que l’exemple suivant, une erreur est désormais générée car le compilateur ne considère pas la seconde fonction comme une spécialisation de la première.

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   Pour corriger ce code, modifiez la seconde fonction :

    ```cpp
    template <> void f(char& val);
    ```

- Le compilateur ne tente plus de supprimer l’ambiguïté des deux fonctions dans l’exemple suivant et émet désormais une erreur :

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   Pour corriger ce code, clarifiez l'appel :

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- Avant la mise en conformité du compilateur avec ISO C++11, le code suivant était compilé et entraînait la résolution de `x` en type **int** :

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Ce code résout maintenant `x` en type `std::initializer_list<int>` et provoque une erreur sur la ligne suivante qui tente d'assigner `x` au type **int**. (Il n'existe pas de conversion par défaut.) Pour corriger ce code, remplacez **auto** par **int** :

    ```cpp
    int x = {0};
    int y = x;
    ```

- L’initialisation d’agrégats n’est plus autorisée quand le type de la valeur de droite ne correspond pas au type de la valeur de gauche qui est initialisée, et une erreur est émise car la norme ISO C++11 requiert une initialisation uniforme pour fonctionner sans conversions restrictives. Auparavant, si une conversion restrictive était possible, un avertissement [avertissement du compilateur (niveau 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) était émis au lieu d’une erreur.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   Pour corriger le code, ajoutez une conversion restrictive explicite :

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- L’initialisation suivante n’est plus autorisée :

    ```cpp
    void *p = {{0}};
    ```

   Pour corriger ce code, utilisez l'une de ces formes :

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- La recherche de nom a changé. Le code suivant est résolu différemment dans le compilateur C++ au sein de Visual Studio 2012 et de Visual Studio 2013 :

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   Dans Visual Studio 2012, `E1` dans l’expression `E1::b` était résolu en `::E1` dans la portée globale. Dans Visual Studio 2013, `E1` dans l’expression `E1::b` correspond à la définition `typedef E2` dans `main()` et a le type `::E2`.

- La disposition des objets a changé. Sur x64, la disposition des objets d'une classe peut changer par rapport aux versions précédentes. Si elle a une fonction **virtuelle** mais n’a pas de classe de base avec une fonction **virtuelle**, le modèle objet du compilateur insère un pointeur vers une table de fonctions **virtuelles** après la disposition des membres de données. Cela signifie que la disposition peut ne pas être optimale dans tous les cas. Dans les versions précédentes, une optimisation pour x64 tentait d’améliorer la disposition pour vous, mais comme elle ne fonctionnait pas correctement dans les cas complexes de code, elle a été supprimée de Visual Studio 2013. Par exemple, prenons le code suivant :

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- Dans Visual Studio 2013, le résultat de `sizeof(S2)`sur x64 est 48 mais, dans les versions précédentes, il est de 32. Pour avoir un résultat égal à 32 dans le compilateur C++ de Visual Studio 2013 pour x64, ajoutez une classe de base factice ayant une fonction **virtuelle** :

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Pour rechercher les emplacements dans votre code qu'une version antérieure aurait essayé d'optimiser, utilisez un compilateur de cette version avec l'option de compilateur `/W3` et activez l'avertissement 4370. Par exemple :

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Dans les versions antérieures à Visual Studio 2013, ce code génère le message : « avertissement C4370 : 'S2' : la disposition de classe a changé par rapport à une version précédente du compilateur en raison d'une meilleure compression ».

   Le compilateur x86 a le même problème de disposition non optimale dans toutes les versions du compilateur. Par exemple, si le code ci-dessous est compilé pour x86 :

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Le résultat de `sizeof(S)` est égal à 24. Toutefois, il peut être réduit à 16 si vous utilisez la solution de contournement mentionnée pour x64 :

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>Bibliothèque standard

Le compilateur C++ dans Visual Studio 2013 détecte des incompatibilités dans _ITERATOR_DEBUG_LEVEL, qui a été implémenté dans Visual Studio 2010, ainsi que des incompatibilités RuntimeLibrary. Ces incompatibilités se produisent quand les options de compilateur `/MT` (version statique), `/MTd` (débogage statique), `/MD` (version dynamique) et `/MDd` (débogage dynamique) sont combinées.

- Si votre code accepte les modèles d’alias simulés de la version antérieure, vous devez le modifier. Par exemple, au lieu de `allocator_traits<A>::rebind_alloc<U>::other`, vous devez indiquer `allocator_traits<A>::rebind_alloc<U>`. Bien que `ratio_add<R1, R2>::type` ne soit plus nécessaire et qu'il vous soit maintenant recommandé d'indiquer `ratio_add<R1, R2>`, le code précédent peut encore être compilé car `ratio<N, D>` doit posséder un typedef « type » pour un taux réduit, qui sera le même type s'il est déjà réduit.

- Vous devez utiliser `#include <algorithm>` lorsque vous appelez `std::min()` ou `std::max()`.

- Si votre code existant utilise les énumérations délimitées simulées de la version antérieure (des énumérations non délimitées classiques encapsulées dans des espaces de noms), vous devez le modifier. Par exemple, si vous faisiez référence au type `std::future_status::future_status`, vous devez indiquer `std::future_status`. Toutefois, la plupart du code reste inchangé. Par exemple, `std::future_status::ready` est encore compilé.

- `explicit operator bool()` est plus strict qu’operator unspecified-bool-type(). `explicit operator bool()` autorise les conversions explicites en type bool (par exemple, avec `shared_ptr<X> sp`, `static_cast<bool>(sp)` et `bool b(sp)` sont valides), ainsi que les « conversions contextuelles » booléennes testables en type bool (par exemple, `if (sp)`, `!sp`, `sp &&`). Toutefois, `explicit operator bool()` n’autorise pas les conversions implicites en type bool. Vous ne pouvez donc pas indiquer `bool b = sp;`, ni indiquer `return sp` avec un type de retour bool.

- Maintenant que de véritables modèles variadiques sont implémentés, _VARIADIC_MAX et les macros connexes n’ont aucun effet. Si vous définissez encore _VARIADIC_MAX, il est ignoré. Si vous avez accepté notre mécanisme de macros destiné à prendre en charge d'une autre façon les modèles variadiques simulés, vous devez modifier votre code.

- En plus des mots clés ordinaires, les en-têtes de la bibliothèque C++ standard n’acceptent plus maintenant le remplacement par macro des mots clés contextuels **override** et **final**.

- `reference_wrapper`, `ref()` et `cref()` interdisent désormais toute liaison aux objets temporaires.

- \<random> applique désormais strictement ses conditions préalables de compilation.

- Différents traits de type de la bibliothèque C++ standard ont la condition préalable « T sera un type complet ». Bien que le compilateur applique désormais cette condition préalable plus strictement, il peut ne pas l’appliquer dans toutes les situations. (Comme les violations de condition préalable de la bibliothèque C++ standard déclenchent un comportement indéfini, Standard ne garantit pas la mise en vigueur.)

- La bibliothèque C++ standard ne prend pas en charge `/clr:oldSyntax`.

- La spécification C++11 pour common_type<> a eu des conséquences inattendues et indésirables. En particulier, common_type\<int, int>::type a retourné int&&. Ainsi, le compilateur implémente la Résolution proposée pour le problème 2141 du groupe de travail de bibliothèque, qui fait que common_type\<int, int="">::type retourne int.

   Effet secondaire de cette modification, le cas d’identité ne s’exécute plus (common_type\<T> ne produit pas toujours le type T). Ce comportement est conforme à la résolution proposée, mais casse le code qui était fondé sur le comportement précédent.

   Si vous avez besoin d’un trait de type d’identité, n’utilisez pas le trait `std::identity` non standard défini dans \<type_traits>, car il ne fonctionne pas pour \<void>. À la place, implémentez votre propre caractéristique de type d'identité pour répondre à vos besoins. Voici un exemple :

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC et ATL

- **Visual Studio 2013 uniquement** : la bibliothèque MFC MBCS n’est pas incluse dans Visual Studio, car Unicode est très répandu et l’utilisation de MBCS a considérablement diminué. Cette modification maintient également MFC plus étroitement aligné avec le Kit de développement logiciel (SDK) Windows, car la plupart des nouveaux contrôles et messages sont seulement Unicode. Toutefois, si vous devez continuer à utiliser la bibliothèque MFC MBCS, vous pouvez la télécharger depuis le Centre de téléchargement MSDN à la page [Bibliothèque MFC multioctets pour Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770). Le package redistribuable Visual C++ inclut toujours cette bibliothèque.  (Remarque : La DLL MBCS est fournie avec les composants d’installation de C++ dans Visual Studio 2015 et les versions ultérieures).

- L’accessibilité pour le ruban MFC est modifiée.  Au lieu d’une architecture d’un niveau, il y a maintenant une architecture hiérarchique. Vous pouvez continuer à utiliser l'ancien comportement en appelant `CRibbonBar::EnableSingleLevelAccessibilityMode()`.

- La méthode `CDatabase::GetConnect` est supprimée. Pour améliorer la sécurité, la chaîne de connexion est maintenant stockée sous forme chiffrée et est déchiffrée uniquement si nécessaire ; elle ne peut pas être retournée sous forme de texte brut.  La chaîne peut être obtenue à l’aide de la méthode `CDatabase::Dump`.

- La signature de `CWnd::OnPowerBroadcast` a changé. La signature de ce gestionnaire de messages est modifiée pour accepter un LPARAM comme deuxième paramètre.

- Les signatures sont modifiées pour prendre en compte les gestionnaires de messages. Les listes de paramètres des fonctions suivantes ont été modifiées pour utiliser des gestionnaires de messages ON_WM_* récemment ajoutés :

   - `CWnd::OnDisplayChange` est remplacé par (UINT, int, int) au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_DISPLAYCHANGE puisse être utilisée dans la table des messages.

   - `CFrameWnd::OnDDEInitiate` est remplacé par (CWnd*, UINT, UNIT) au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_DDE_INITIATE puisse être utilisée dans la table des messages.

   - `CFrameWnd::OnDDEExecute` est remplacé par (CWnd*, HANDLE) au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_DDE_EXECUTE puisse être utilisée dans la table des messages.

   - `CFrameWnd::OnDDETerminate` est remplacé par (CWnd*) comme paramètre au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_DDE_TERMINATE puisse être utilisée dans la table des messages.

   - `CMFCMaskedEdit::OnCut` est remplacé par aucun paramètre au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_CUT puisse être utilisée dans la table des messages.

   - `CMFCMaskedEdit::OnClear` est remplacé par aucun paramètre au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_CLEAR puisse être utilisée dans la table des messages.

   - `CMFCMaskedEdit::OnPaste` est remplacé par aucun paramètre au lieu de (WPARAM, LPARAM) afin que la nouvelle macro ON_WM_PASTE puisse être utilisée dans la table des messages.

- Les directives `#ifdef`dans les fichiers d’en-tête MFC sont supprimées. De nombreuses directives &lt; dans les fichiers d’en-tête MFC liées aux versions de Windows non prises en charge (WINVER `#ifdef` 0x0501) sont supprimées.

- DLL ATL (atl120.dll) est supprimée. La bibliothèque ATL est maintenant fournie en tant qu'en-têtes et que bibliothèque statique (atls.lib).

- Atlsd.lib, atlsn.lib et atlsnd.lib sont supprimées. Atls.lib n'a plus de dépendances de jeu de caractères ou de code spécifique pour debug/release. Étant donné qu'elle fonctionne de la même manière pour l'Unicode/ANSI et debug/release, une seule version de la bibliothèque est requise.

- L’outil ATL/MFC Trace Tool est supprimé avec la DLL ATL, et le mécanisme de traçage est simplifié. Le constructeur `CTraceCategory` accepte maintenant un paramètre (nom de catégorie), et les macros TRACE appellent des fonctions de création de rapports de débogage CRT.

## <a name="visual-c-2012-breaking-changes"></a>Modifications avec rupture dans Visual C++ 2012

### <a name="compiler"></a>Compilateur

- L’option de compilateur `/Yl` a changé. Par défaut, le compilateur utilise cette option, qui peut entraîner des erreurs LNK2011 sous certaines conditions. Pour plus d’informations, consultez [/Yl (Injecter une référence PCH pour une bibliothèque de débogage)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- Dans le code compilé avec `/clr`, le mot clé de classe **enum** définit un enum C++11 et non un enum CLR (Common Language Runtime). Pour définir un enum CLR, vous devez être explicite sur son accessibilité.

- Utilisez le mot clé template pour supprimer explicitement l’ambiguïté d’un nom dépendant (conformité à la norme du langage C++). Dans l’exemple suivant, le mot clé template en surbrillance est obligatoire pour résoudre l’ambiguïté. Pour plus d’informations, consultez [Résolution de noms pour les types dépendants](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Une expression constante de type float n’est plus autorisée comme argument template, comme illustré dans l’exemple suivant.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Le code qui est compilé à l’aide de l’option de ligne de commande `/GS` et qui présente une vulnérabilité de type « off-by-one » peut provoquer l’arrêt du processus au moment de l’exécution, comme indiqué dans l’exemple de pseudo-code suivant.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- L’architecture par défaut pour les builds x86 devient SSE2 ; par conséquent, le compilateur peut émettre des instructions SSE et utilise les registres XMM pour effectuer des calculs à virgule flottante. Si vous souhaitez rétablir le comportement précédent, utilisez l’indicateur de compilateur `/arch:IA32` pour spécifier l’architecture IA32.

- Le compilateur peut émettre des avertissements [avertissement du compilateur (niveau 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) et C4701 là où il ne le faisait pas précédemment. Le compilateur effectue des vérifications plus strictes pour l’utilisation de variables locales non initialisées de type pointeur.

- Quand le nouvel indicateur d’éditeur de liens `/HIGHENTROPYVA` est spécifié, les allocations de mémoire dans Windows 8 retournent en général une adresse 64 bits. (Avant Windows 8, ces allocations retournaient le plus souvent des adresses inférieures à 2 Go.) Ce changement peut exposer des bogues de troncation de pointeur dans le code existant. Par défaut, ce commutateur est activé. Pour désactiver ce comportement, spécifiez `/HIGHENTROPYVA:NO`.

- Le compilateur managé (Visual Basic/C#) prend également en charge `/HIGHENTROPYVA` pour les builds managées.  Toutefois, dans ce cas, le commutateur `/HIGHENTROPYVAswitch` est désactivé par défaut.

### <a name="ide"></a>IDE

- Même si nous vous déconseillons de créer des applications Windows Forms en C++/CLI, la gestion des applications d’interface utilisateur C++/CLI existantes est prise en charge. Si vous devez créer une application Windows Forms, ou toute autre application d’interface utilisateur .NET, utilisez C# ou Visual Basic. Utilisez C++/CLI à des fins d’interopérabilité uniquement.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Bibliothèque de modèles parallèles et bibliothèque runtime d’accès concurrentiel

L’énumération `SchedulerType` d’`UmsThreadDefault` est dépréciée. La spécification d’`UmsThreadDefault` génère un avertissement déprécié et est remappée en interne à `ThreadScheduler`.

### <a name="standard-library"></a>Bibliothèque standard

- En raison d’un changement cassant entre les normes C++98/03 et C++11, l’utilisation d’arguments template explicites pour appeler `make_pair()` (comme dans `make_pair<int, int>(x, y)`) ne permet généralement pas la compilation en Visual C++ dans Visual Studio 2012. La solution consiste à toujours appeler `make_pair() ` sans arguments template explicites, comme dans `make_pair(x, y)`. L’indication d’arguments template explicites va à l’encontre de l’objectif de la fonction. Si vous avez besoin d’un contrôle précis sur le type résultant, utilisez `pair` au lieu de `make_pair`, comme dans `pair<short, short>(int1, int2)`.

- Autre changement cassant entre les normes C++98/03 et C++11 : quand A est implicitement convertible en B et B est implicitement convertible en C, mais quand A n’est pas implicitement convertible en C, C++98/03 et Visual C++ 2010 autorisaient la conversion (implicite ou explicite) de `pair<A, X>` en `pair<C, X>`. (L’autre type, X, ne présente pas d’intérêt ici, et n’est pas propre au premier type de la paire.) Le compilateur C++ dans Visual Studio 2012 détecte que A n’est pas implicitement convertible en C, et supprime la conversion de paire de la résolution de surcharge. Ce changement est positif dans de nombreux scénarios. Par exemple, la surcharge de `func(const pair<int, int>&)` et `func(const pair<string, string>&)`, et l’appel de `func()` avec `pair<const char *, const char *>`, permettent maintenant la compilation. Toutefois, cette modification altère le code qui reposait sur des conversions de paires agressives. Ce code peut généralement être corrigé en effectuant une partie de la conversion explicitement, par exemple, en passant `make_pair(static_cast<B>(a), x)` à une fonction qui attend `pair<C, X>`.

- Visual C++ 2010 simulait des modèles variadiques, par exemple `make_shared<T>(arg1, arg2, argN)`, jusqu’à une limite de 10 arguments, en marquant les surcharges et les spécialisations avec le mécanisme de préprocesseur. Dans Visual Studio 2012, cette limite est réduite à cinq arguments pour améliorer les temps de compilation et la consommation de mémoire du compilateur pour la majorité des utilisateurs. Toutefois, vous pouvez définir la limite précédente en affectant explicitement 10 à _VARIADIC_MAX, au niveau du projet.

- C++11 17.6.4.3.1 [macro.names]/2 interdit le remplacement par macro des mots clés quand les en-têtes de la bibliothèque C++ standard sont inclus. Les en-têtes émettent maintenant des erreurs de compilateur s’ils détectent des mots clés remplacés par macro. (La définition de _ALLOW_KEYWORD_MACROS permet de compiler ce code, mais nous vous déconseillons vivement cette utilisation.) En guise d’exception, la forme macro de `new` est autorisée par défaut, car les en-têtes se défendent intégralement à l’aide de `#pragma push_macro("new")`/`#undef new`/`#pragma pop_macro("new")`. La définition de _ENFORCE_BAN_OF_MACRO_NEW fait exactement ce que son nom indique.

- Pour implémenter différentes optimisations et vérifications de débogage, l’implémentation de la bibliothèque C++ standard interrompt intentionnellement la compatibilité binaire entre les versions de Visual Studio (2005, 2008, 2010, 2012). Quand la bibliothèque C++ standard est utilisée, elle interdit de combiner les fichiers objets et les bibliothèques statiques qui sont compilés à l’aide de différentes versions en un seul fichier binaire (EXE ou DLL), et aussi de transmettre les objets de la bibliothèque C++ standard entre des fichiers binaires compilés à l’aide de différentes versions. Avec la bibliothèque C++ standard, l’association de fichiers objets et de bibliothèques statiques qui ont été compilés en utilisant Visual C++ 2010 à ceux qui ont été compilés en utilisant le compilateur C++ dans Visual Studio 2012 génère des erreurs d’éditeur de liens sur l’incompatibilité de _MSC_VER, où _MSC_VER est la macro qui contient la version principale du compilateur (1700 pour Visual C++ dans Visual Studio 2012). Cette vérification ne peut pas détecter les combinaisons de DLL et ne peut pas détecter les combinaisons impliquant Visual C++ 2008 ou version antérieure.

- Outre la détection des incompatibilités dans _ITERATOR_DEBUG_LEVEL, qui a été implémenté dans Visual C++ 2010, le compilateur C++ dans Visual Studio 2012 détecte les incompatibilités de la bibliothèque runtime. Elles se produisent quand les options de compilateur `/MT` (version statique), `/MTd` (débogage statique), `/MD` (version dynamique) et `/MDd` (débogage dynamique) sont combinées.

- Avant, `operator<()`, `operator>()`, `operator<=()` et `operator>=()` étaient disponibles pour les familles de conteneurs `std::unordered_map` et `stdext::hash_map`, même si leurs implémentations n’étaient pas utiles. Ces opérateurs non standard ont été supprimés en Visual C++ dans Visual Studio 2012. De plus, l’implémentation de `operator==()` et `operator!=()` pour la famille `std::unordered_map` a été étendue à la famille `stdext::hash_map`. (Nous vous recommandons d’éviter d’utiliser la famille `stdext::hash_map` dans le nouveau code.)

- C++11 22.4.1.4 [locale.codecvt] spécifie que `codecvt::length()` et `codecvt::do_length()` doivent accepter des paramètres `stateT&` modifiables, mais Visual C++ 2010 a pris `const stateT&`. Le compilateur C++ dans Visual Studio 2012 accepte `stateT&` comme l’exige la norme. Cette différence est importante pour quiconque tente de remplacer la fonction virtuelle `do_length()`.

### <a name="crt"></a>CRT

- Le tas Runtime C (CRT), qui est utilisé pour new et malloc(), n’est plus privé. La bibliothèque CRT utilise désormais le tas de processus. Cela signifie que le tas n’étant pas détruit quand une DLL est déchargée, les DLL qui sont liées statiquement à la bibliothèque CRT doivent vérifier que la mémoire qui est allouée par le code de la DLL est nettoyée avant d’être déchargée.

- L’assertion de la fonction `iscsymf()` donne des valeurs négatives.

- Le struct `threadlocaleinfostruct` a changé pour prendre en compte les modifications apportées aux fonctions de paramètres régionaux.

- Les fonctions CRT qui ont des fonctions intrinsèques correspondantes comme `memxxx()`, `strxxx()` sont supprimées d’intrin.h. Si vous avez inclus intrin.h uniquement pour ces fonctions, vous devez maintenant inclure les en-têtes CRT correspondants.

### <a name="mfc-and-atl"></a>MFC et ATL

- Suppression de la prise en charge de Fusion (afxcomctl32.h) ; par conséquent, toutes les méthodes qui sont définies dans \<afxcomctl32.h> ont été supprimées. Les fichiers d’en-tête \<afxcomctl32.h> et \<afxcomctl32.inl> ont été supprimés.

- Renommage de `CDockablePane::RemoveFromDefaultPaneDividier` en `CDockablePane::RemoveFromDefaultPaneDivider`.

- Changement de la signature de `CFileDialog::SetDefExt` pour utiliser LPCTSTR. Par conséquent, les builds Unicode sont impactées.

- Suppression des catégories de traçage ATL obsolètes.

- Changement de la signature de `CBasePane::MoveWindow` pour utiliser une `const CRect`.

- Changement de la signature de `CMFCEditBrowseCtrl::EnableBrowseButton`.

- Suppression de `m_fntTabs` et de `m_fntTabsBold` dans `CMFCBaseTabCtrl`.

- Ajout d’un paramètre aux constructeurs `CMFCRibbonStatusBarPane`. (Comme il s’agit d’un paramètre par défaut, il ne casse pas la source.)

- Ajout d’un paramètre au constructeur `CMFCRibbonCommandsListBox`. (Comme il s’agit d’un paramètre par défaut, il ne casse pas la source.)

- Suppression de l’API `AFXTrackMouse` (et du proc de minuterie associé). Utilisez l’API Win32 `TrackMouseEvent` à la place.

- Ajout d’un paramètre au constructeur `CFolderPickerDialog`. (Comme il s’agit d’un paramètre par défaut, il ne casse pas la source.)

- Changement de la taille de la structure `CFileStatus` : le membre `m_attribute` a été changé de BYTE en DWORD (pour correspondre à la valeur qui est retournée de `GetFileAttributes`).

- `CRichEditCtrl` et `CRichEditView` utilisent MSFTEDIT_CLASS (contrôle RichEdit 4.1) au lieu de RICHEDIT_CLASS (contrôle RichEdit 3.0) dans les builds Unicode.

- Suppression de `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground`, car sa valeur est toujours TRUE sur Windows Vista, Windows 7 et Windows 8.

- Suppression de `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable`, car sa valeur est toujours TRUE sur Windows Vista, Windows 7 et Windows 8.

- Suppression de `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Appelez l’API Windows directement sur Windows Vista, Windows 7 et Windows 8.

- Suppression de `AFX_GLOBAL_DATA::DwmDefWindowProc`. Appelez l’API Windows directement sur Windows Vista, Windows 7 et Windows 8.

- Renommage de `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` en `IsDwmCompositionEnabled` pour éliminer toute collision de nom.

- Changement des identificateurs pour plusieurs minuteries internes MFC et déplacement des définitions vers afxres.h (AFX_TIMER_ID_*).

- Changement de la signature de la méthode `OnExitSizeMove` pour concorder avec la macro ON_WM_EXITSIZEMOVE :

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Changement du nom et de la signature de `OnDWMCompositionChanged` pour concorder avec la macro ON_WM_DWMCOMPOSITIONCHANGED :

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Changement de la signature de la méthode `OnMouseLeave` pour concorder avec la macro ON_WM_MOUSELEAVE :

   - `CMFCCaptionBar`

   - `CMFCColorBar`

   - `CMFCHeaderCtrl`

   - `CMFCProperySheetListBox`

   - `CMFCRibbonBar`

   - `CMFCRibbonPanelMenuBar`

   - `CMFCRibbonRichEditCtrl`

   - `CMFCSpinButtonCtrl`

   - `CMFCToolBar` ReplaceThisText

   - `CMFCToolBarComboBoxEdit`

   - `CMFCToolBarEditCtrl`

   - `CMFCAutoHideBar`

- Changement de la signature de la méthode `OnPowerBroadcast` pour concorder avec la macro ON_WM_POWERBROADCAST :

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- Changement de la signature de la méthode `OnStyleChanged` pour concorder avec la macro ON_WM_STYLECHANGED :

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- Renommage de la méthode interne `FontFamalyProcFonts` en `FontFamilyProcFonts`.

- Suppression de nombreux objets `CString` statiques globaux afin d’éliminer les fuites de mémoire dans certaines situations (remplacés par #defines), et des variables membres de classe suivantes :

   - `CKeyBoardManager::m_strDelimiter`

   - `CMFCPropertyGridProperty::m_strFormatChar`

   - `CMFCPropertyGridProperty::m_strFormatShort`

   - `CMFCPropertyGridProperty::m_strFormatLong`

   - `CMFCPropertyGridProperty::m_strFormatUShort`

   - `CMFCPropertyGridProperty::m_strFormatULong`

   - `CMFCPropertyGridProperty::m_strFormatFloat`

   - `CMFCPropertyGridProperty::m_strFormatDouble`

   - `CMFCToolBarImages::m_strPngResType`

   - `CMFCPropertyGridProperty::m_strFormat`

- Changement de la signature de `CKeyboardManager::ShowAllAccelerators` et suppression du paramètre délimiteur d’accélérateur.

- Ajout de `CPropertyPage::GetParentSheet` et, dans la classe `CPropertyPage`, appel de cette dernière au lieu de `GetParent` pour obtenir la fenêtre de feuille parente correcte, qui peut être la fenêtre parente ou une fenêtre grand-parente de `CPropertyPage`. Vous devrez peut-être modifier votre code pour appeler `GetParentSheet` au lieu de `GetParent`.

- Correction du #pragma warning(push) déséquilibré dans ATLBASE.H, qui entraînait une désactivation incorrecte des avertissements. Ces avertissements sont désormais activés correctement après l’analyse d’ATLBASE.H.

- Déplacement des méthodes D2D depuis AFX_GLOBAL_DATA vers _AFX_D2D_STATE :

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - Par exemple, au lieu d’appeler `afxGlobalData.IsD2DInitialized`, appelez `AfxGetD2DState->IsD2DInitialized`.

- Suppression des fichiers ATL*.CPP obsolètes du dossier \atlmfc\include\.

- Initialisation d’`DLLMain` à la demande, et non plus au moment de l’initialisation CRT, pour répondre aux exigences de `afxGlobalData`.

- Ajout de la méthode `RemoveButtonByIndex` à la classe `CMFCOutlookBarPane`.

- Correction de `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` en `IsFrequentlyUsedCmd`.

- Correction de plusieurs instances de `RestoreOriginalstate` en `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`.

- Suppression des méthodes inutilisées de `CDockablePane` : `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo` et `CanAdjustLayout`.

- Suppression des variables membres statiques de `CDockablePane` : `m_bCaptionText` et `m_bHideDisabledButtons`.

- Ajout d’une méthode `DeleteString` override à `CMFCFontComboBox`.

- Suppression des méthodes inutilisées de `CPane` : `GetMinLength` et `IsLastPaneOnLastRow`.

- Renommage de `CPane::GetDockSiteRow(CDockingPanesRow *)` en `CPane::SetDockSiteRow`.

## <a name="visual-c-2010-breaking-changes"></a>Modifications avec rupture dans Visual C++ 2010

### <a name="compiler"></a>Compilateur

- Le mot clé **auto** a une nouvelle signification par défaut. Étant donné que l’utilisation de l’ancienne signification est rare, la plupart des applications ne seront pas affectées par cette modification.

- Le nouveau mot clé **static_assert** est introduit, ce qui entraîne un conflit de nom s’il existe déjà un identificateur de ce nom dans votre code.

- La prise en charge de la nouvelle notation lambda exclut la prise en charge du codage d’un GUID sans guillemet dans un attribut uuid IDL.

- .NET Framework 4 introduit le concept d’exceptions d’état endommagé, qui sont des exceptions qui laissent un processus dans un état endommagé irrécupérable. Par défaut, vous ne pouvez pas intercepter une exception d’état endommagé, même avec l’option de compilateur /EHa qui intercepte toutes les autres exceptions.                 Pour intercepter explicitement une exception d’état endommagé, utilisez les instructions __try-\__except. Sinon, appliquez l’attribut [HandledProcessCorruptedStateExceptions] pour permettre à une fonction d’intercepter des exceptions d’état endommagé.  Cette modification affecte essentiellement les programmeurs système qui devront peut-être intercepter une exception d’état endommagé. Les huit exceptions sont STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, STATUS_UNWIND_CONSOLIDATE.                 Pour plus d’informations sur ces exceptions, consultez la macro [GetExceptionCode](/windows/desktop/Debug/getexceptioncode).

- L’option de compilateur `/GS` modifiée protège contre les dépassements de mémoire tampon d’une manière plus complète que dans les versions antérieures. Cette version peut introduire des vérifications de sécurité supplémentaires dans la pile qui peuvent nuire aux performances. Utilisez le nouveau mot clé `__declspec(safebuffers)` pour indiquer au compilateur de ne pas insérer de vérifications de sécurité pour une fonction particulière.

- Si, pour la compilation, vous utilisez les deux options de compilateur `/GL` (Optimisation de l’ensemble du programme) et `/clr` (Compilation pour le Common Language Runtime), l’option `/GL` est ignorée. Cette modification a été apportée parce que la combinaison d’options de compilateur offrait peu d’avantages. Suite à cette modification, les performances de la build se sont améliorées.

- Par défaut, la prise en charge des trigraphes est désactivée dans Visual C++ 2010. Utilisez l’option de compilateur `/Zc:trigraphs` pour activer la prise en charge des trigraphes. Un trigraphe se compose de deux points d’interrogation consécutifs (??) suivis d’un troisième caractère unique. Le compilateur remplace un trigraphe par un caractère de ponctuation correspondant. Par exemple, le compilateur remplace le trigraphe `??=` par le signe dièse « # ». Utilisez des trigraphes dans les fichiers sources C qui utilisent un jeu de caractères qui ne contient pas de représentation graphique pour certains caractères de ponctuation.

- L’éditeur de liens ne prend plus en charge l’optimisation pour Windows 98. L’option `/OPT` (Optimisations) provoque une erreur au moment de la compilation si vous spécifiez `/OPT:WIN98` ou `/OPT:NOWIN98`.

- Les options de compilateur par défaut spécifiées par les propriétés de système de génération RuntimeLibrary et DebugInformationFormat ont été modifiées. Par défaut, ces propriétés de génération sont spécifiées dans les projets créés par Visual C++ versions 7.0 à 10.0. Si vous migrez un projet créé par Visual C++ 6.0, déterminez s’il est nécessaire de spécifier une valeur pour ces propriétés.

- Dans Visual C++ 2010, RuntimeLibrary = MultiThreaded (`/MD`) et DebugInformationFormat = ProgramDatabase (`/Zi`). Dans Visual C++ 9.0, RuntimeLibrary = MultiThreaded (`/MT`) et DebugInformationFormat = Disabled.

### <a name="clr"></a>CLR

- Les compilateurs Microsoft C# et Visual Basic peuvent désormais produire un assembly non-PIA (Primary Interop Assembly). Un assembly non-PIA peut utiliser des types COM sans le déploiement de l’assembly PIA pertinent. Lors de la consommation des assemblys non-PIA produits par Visual C# ou Visual Basic, vous devez référencer l’assembly PIA sur la commande de compilation avant de référencer un assembly non-PIA qui utilise la bibliothèque.

### <a name="visual-c-projects-and-msbuild"></a>Projets Visual C++ et MSBuild

- Les projets Visual C++ sont désormais basés sur l’outil MSBuild. Par conséquent, les fichiers projet utilisent un nouveau format de fichier XML et un suffixe de fichier .vcxproj. Visual C++ 2010 convertit automatiquement les fichiers projet des versions antérieures de Visual Studio vers le nouveau format de fichier. Un projet existant est affecté s’il dépend de l’outil de génération précédent, VCBUILD.exe, ou du suffixe de fichier projet, .vcproj.

- Dans les versions antérieures, Visual C++ prenait en charge l’évaluation tardive des feuilles de propriétés. Par exemple, une feuille de propriétés parente pouvait importer une feuille de propriétés enfant, et le parent pouvait utiliser une variable définie dans l’enfant pour définir d’autres variables. L’évaluation tardive permettait au parent d’utiliser la variable enfant avant même que la feuille de propriétés enfant ne soit importée. Dans Visual C++ 2010, une variable de la feuille du projet ne peut pas être utilisée avant d’être définie, car MSBuild prend uniquement en charge l’évaluation anticipée.

### <a name="ide"></a>IDE

- La boîte de dialogue de fin de l’application n’arrête plus une application. Dans les versions précédentes, quand la fonction `abort()` ou `terminate()` fermait la version commerciale d’une application, la bibliothèque Runtime C affichait un message d’arrêt de l’application dans une fenêtre de console ou une boîte de dialogue. Le message indiquait en partie que l’application avait demandé son arrêt au Runtime d’une façon inhabituelle. L’utilisateur pouvait contacter l’équipe du support technique de l’application pour plus d’informations. Le message d’arrêt de l’application était redondant parce que Windows affichait ensuite le gestionnaire d’arrêt actif qui était habituellement la boîte de dialogue Rapport d’erreurs Windows (Dr. Watson) ou le débogueur Visual Studio. À partir de Visual Studio 2010, la bibliothèque Runtime C n’affiche plus le message. En outre, le Runtime empêche l’arrêt de l’application avant le démarrage d’un débogueur. Il s’agit d’un changement cassant uniquement si votre code dépend encore de l’ancien comportement du message d’arrêt de l’application.

- Dans le cas particulier de Visual Studio 2010, IntelliSense ne fonctionne pas pour les attributs ou le code C++/CLI, **Rechercher toutes les références** ne fonctionne pas pour les variables locales, et le modèle de code ne récupère pas les noms de type des assemblys importés ni ne convertit les types en leurs noms qualifiés complets.

### <a name="libraries"></a>Bibliothèques

- La classe SafeInt est incluse dans Visual C++ et n’est plus disponible en téléchargement séparé. Il s’agit d’un changement cassant uniquement si vous avez développé une classe qui est également nommée « SafeInt ».

- Le modèle de déploiement de bibliothèques n’utilise plus les manifestes pour rechercher une version particulière d’une bibliothèque de liens dynamiques. Au lieu de cela, le nom de chaque bibliothèque de liens dynamiques contient son numéro de version, et vous utilisez ce nom pour trouver la bibliothèque.

- Dans les versions précédentes de Visual Studio, vous pouviez régénérer les bibliothèques Runtime. Visual C++ 2010 ne prend plus en charge la génération de vos propres copies des fichiers de la bibliothèque Runtime C.

### <a name="standard-library"></a>Bibliothèque standard

- L’en-tête \<iterator> n’est plus inclus automatiquement par de nombreux autres fichiers d’en-tête. Incluez plutôt cet en-tête explicitement si vous avez besoin de prendre en charge les itérateurs autonomes définis dans l’en-tête. Un projet existant est affecté s’il dépend de l’outil de génération précédent, VCBUILD.exe, ou du suffixe de fichier projet, .vcproj.iterator.

- Dans l’en-tête \<algorithm>, les fonctions checked_* et unchecked_\* sont supprimées. Dans l’en-tête \<iterator>>, la classe `checked_iterator` a été supprimée et la classe `unchecked_array_iterator` a été ajoutée.

- Le constructeur `CComPtr::CComPtr(int)` est supprimé. Ce constructeur permettait de construire un objet `CComPtr` à partir de la macro NULL, mais il était inutile et autorisait des constructions absurdes à partir d’entiers non nuls.

   Un objet `CComPtr` peut toujours être construit à partir de la macro NULL, qui a la valeur 0, mais il échouera s’il est construit à partir d’un entier autre que le littéral 0. Utilisez **nullptr** à la place.

- Les fonctions membres `ctype` suivantes ont été supprimées : `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s`. Si une application utilise l’une de ces fonctions membres, vous devez la remplacer par la version non sécurisée correspondante : `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`.

### <a name="crt-mfc-and-atl-libraries"></a>Bibliothèques CRT, MFC et ATL

- La prise en charge de la génération des bibliothèques CRT, MFC et ATL par les utilisateurs a été supprimée. Par exemple, aucun fichier NMAKE approprié n’est fourni. Toutefois, les utilisateurs ont encore accès au code source pour ces bibliothèques. En outre, un document qui décrit les options MSBuild utilisées par Microsoft pour générer ces bibliothèques sera vraisemblablement publié dans un blog de l’équipe Visual C++.

- La prise en charge MFC pour IA64 a été supprimée. Toutefois, une prise en charge de CRT et ATL sur IA64 est encore disponible.

- Les ordinaux ne sont plus réutilisés dans les fichiers de définition de module (.def) MFC. Cette modification signifie qu’il n’y aura pas de différence entre les ordinaux des versions secondaires, et que la compatibilité binaire pour les Service Packs et les versions de correctif QFE sera améliorée.

- Une nouvelle fonction virtuelle a été ajoutée à la classe `CDocTemplate`. Il s’agit de [CDocTemplate Class](../mfc/reference/cdoctemplate-class.md). La version précédente d’`OpenDocumentFile` avait deux paramètres. La nouvelle version en a trois. Pour prendre en charge le gestionnaire de redémarrage, toute classe dérivée de `CDocTemplate` doit implémenter la version ayant trois paramètres. Le nouveau paramètre est `bAddToMRU`.

### <a name="macros-and-environment-variables"></a>Macros et variables d’environnement

- La variable d’environnement __MSVCRT_HEAP_SELECT n’est plus prise en charge. Cette variable d’environnement est supprimée et rien ne la remplace.

### <a name="microsoft-macro-assembler-reference"></a>Référence de Microsoft Macro Assembler

- Plusieurs directives ont été supprimées du compilateur Référence de Microsoft Macro Assembler. Les directives supprimées sont `.186`, `.286`, `.286P`, `.287`, `.8086`, `.8087` et `.NO87`.

## <a name="visual-c-2008-breaking-changes"></a>Modifications avec rupture dans Visual C++ 2008

### <a name="compiler"></a>Compilateur

- Les plateformes Windows 95, Windows 98, Windows ME et Windows NT ne sont plus prises en charge. Ces systèmes d’exploitation ont été supprimés de la liste des plateformes ciblées.

- Le compilateur ne prend plus en charge plusieurs attributs qui étaient directement associés à ATL Server. Les attributs suivants ne sont plus pris en charge :

   - perf_counter

   - perf_object

   - perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-c-projects"></a>Projets Visual C++

- Lors de la mise à niveau de projets créés avec des versions antérieures de Visual Studio, vous devrez peut-être modifier les macros WINVER et _WIN32_WINNT afin qu’elles soient supérieures ou égales à 0x0500.

- À partir de Visual Studio 2008, le nouvel Assistant Projet ne permet pas de créer un projet SQL Server en C++. Les projets SQL Server créés à l’aide d’une version antérieure de Visual Studio seront cependant compilés et fonctionneront toujours correctement.

- Le fichier d’en-tête API Windows Winable.h a été supprimé. Incluez à la place Winuser.h.

- La bibliothèque API Windows Rpcndr.lib a été supprimée. Établissez la liaison avec rpcrt4.lib à la place.

### <a name="crt"></a>CRT

- La prise en charge de Windows 95, Windows 98, Windows Millennium Edition et Windows NT 4.0 a été supprimée.

- Les variables globales suivantes ont été supprimées :

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- Les fonctions suivantes ont été supprimées. À la place, utilisez les fonctions API Windows `GetVersion` ou `GetVersionEx` :

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- La syntaxe des annotations SAL a changé. Pour plus d’informations, consultez [Annotations SAL](../c-runtime-library/sal-annotations.md).

- Le filtre IEEE prend désormais en charge le jeu d’instructions SSE 4.1. Pour plus d’informations, consultez [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Les bibliothèques Runtime C fournies avec Visual Studio ne sont plus dépendantes de la DLL système msvcrt.dll.

### <a name="standard-library"></a>Bibliothèque standard

- La prise en charge de Windows 95, Windows 98, Windows Millennium Edition et Windows NT 4.0 a été supprimée.

- Lors de la compilation en mode débogage avec _HAS_ITERATOR_DEBUGGING défini (remplacé par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) après Visual Studio 2010), une application indique maintenant quand un itérateur tente d’effectuer une incrémentation ou décrémentation au-delà des limites du conteneur sous-jacent.

- La variable membre c de la pile Class est maintenant déclarée protected. Auparavant, cette variable membre était déclarée public.

- Le comportement de `money_get::do_get` a changé. Avant, lors de l’analyse d’une valeur monétaire avec plus de chiffres de fraction que `frac_digits` n’en demandait, `do_get` en consommait la totalité. À présent, `do_get` arrête l’analyse juste après la consommation des caractères `frac_digits`.

### <a name="atl"></a>ATL

- Un projet ATL ne peut pas être généré sans une dépendance envers CRT. Dans les versions antérieures de Visual Studio, vous pouviez utiliser #define ATL_MIN_CRT pour rendre un projet ATL à peine dépendant de CRT. Dans Visual C++ 2008, tous les projets ATL sont à peine dépendants de CRT, qu’ATL_MIN_CRT soit défini ou non.

- Le code base ATL Server a été publié comme projet source partagé sur CodePlex et n’est pas installé dans le cadre de Visual Studio. Les classes d’encodage et de décodage de données d’atlenc.h ainsi que les fonctions utilitaires et classes d’atlutil.h et d’atlpath.h ont été conservées et font désormais partie de la bibliothèque ATL. Plusieurs fichiers associés à ATL Server ne font plus partie de Visual Studio.

- Certaines fonctions ne sont plus incluses dans la DLL. Elles se trouvent toujours dans la bibliothèque d’importation. Le code qui utilise les fonctions de manière statique n’est pas affecté. Seul le code qui utilise ces fonctions de manière dynamique est concerné.

- Les macros PROP_ENTRY et PROP_ENTRY_EX ont été dépréciées, et remplacées par les macros PROP_ENTRY_TYPE et PROP_ENTRY_TYPE_EX pour des raisons de sécurité.

### <a name="atlmfc-shared-classes"></a>Classes partagées ATL/MFC

- Un projet ATL ne peut pas être généré sans une dépendance envers CRT. Dans les versions antérieures de Visual Studio, vous pouviez utiliser `#define ATL_MIN_CRT` pour rendre un projet ATL à peine dépendant de CRT. Dans Visual C++ 2008, tous les projets ATL sont à peine dépendants de CRT, qu’ATL_MIN_CRT soit défini ou non.

- Le code base ATL Server a été publié comme projet source partagé sur CodePlex et n’est pas installé dans le cadre de Visual Studio. Les classes d’encodage et de décodage de données d’atlenc.h ainsi que les fonctions utilitaires et classes d’atlutil.h et d’atlpath.h ont été conservées et font désormais partie de la bibliothèque ATL. Plusieurs fichiers associés à ATL Server ne font plus partie de Visual Studio.

- Certaines fonctions ne sont plus incluses dans la DLL. Elles se trouvent toujours dans la bibliothèque d’importation. Le code qui utilise les fonctions de manière statique n’est pas affecté. Seul le code qui utilise ces fonctions de manière dynamique est concerné.

### <a name="mfc"></a>MFC

- Classe `CTime` : la classe `CTime` accepte désormais les dates à partir du 1/1/1900 (notre ère) au lieu du 1/1/1970 (notre ère).

- Ordre de tabulation des contrôles dans les boîtes de dialogue MFC : l’ordre de tabulation correct de plusieurs contrôles dans une boîte de dialogue MFC est perturbé si un contrôle ActiveX MFC est inséré dans l’ordre de tabulation. Cette modification résout ce problème.

   Par exemple, créez une application de boîte de dialogue MFC qui comporte un contrôle ActiveX et plusieurs contrôles d’édition. Placez le contrôle ActiveX au milieu de l’ordre de tabulation des contrôles d’édition. Démarrez l’application, cliquez sur un contrôle d’édition dont l’ordre de tabulation se situe après le contrôle ActiveX et appuyez sur TAB. Avant cette modification, le focus était placé sur le contrôle d’édition suivant le contrôle ActiveX et non sur le contrôle d’édition suivant dans l’ordre de tabulation.

- Classe `CFileDialog` : les modèles personnalisés pour la classe `CFileDialog` ne peuvent pas être automatiquement portés vers Windows Vista. Ils sont toujours utilisables, mais ne présentent pas l’aspect ni les fonctionnalités supplémentaires des boîtes de dialogue de style Windows Vista.

- Classe `CWnd` et classe `CFrameWnd` : la méthode `CWnd::GetMenuBarInfo` a été supprimée.

   La méthode `CFrameWnd::GetMenuBarInfo` est maintenant une méthode non virtuelle. Pour plus d’informations, consultez **GetMenuBarInfo, fonction** dans le SDK Windows.

- Prise en charge d’ISAPI par MFC : MFC ne prend plus en charge la génération d’applications avec l’interface ISAPI (Internet Server Application Programming Interface). Si vous souhaitez générer une application ISAPI, appelez directement les extensions ISAPI.

- API ANSI dépréciées : les versions ANSI de plusieurs méthodes MFC sont dépréciées. Utilisez les versions Unicode de ces méthodes dans vos futures applications. Pour plus d’informations, consultez **Configuration requise pour les contrôles communs Windows Vista**.

## <a name="visual-c-2005-breaking-changes"></a>Modifications avec rupture dans Visual C++ 2005

### <a name="crt"></a>CRT

- De nombreuses fonctions ont été dépréciées. Consultez **Fonctions CRT dépréciées**.

- De nombreuses fonctions valident désormais leurs paramètres et interrompent l’exécution si des paramètres non valides sont fournis. Cette validation peut casser le code qui passe des paramètres non valides et s’appuie sur le fait que la fonction les ignore ou retourne simplement un code d’erreur. Consultez **Validation des paramètres**.

- La valeur de descripteur de fichier -2 est désormais utilisée pour indiquer que `stdout` et `stderr` ne sont pas disponibles pour la sortie, par exemple dans une application Windows qui n’a aucune fenêtre de console. La valeur précédente utilisée était -1. Pour plus d’informations, consultez [_fileno](../c-runtime-library/reference/fileno.md).

- Les bibliothèques CRT monothread (libc.lib et libcd.lib) ont été supprimées. Utilisez les bibliothèques CRT multithread. L’indicateur de compilateur `/ML` n’est plus pris en charge. Des versions non bloquantes de certaines fonctions ont été ajoutées dans les cas où la différence de performances entre le code multithread et le code monothread est potentiellement significative.

- La surcharge de pow, double pow(int, int) a été supprimée pour une meilleure conformité à la norme.

- Le spécificateur de format %n n’est plus pris en charge par défaut dans aucune famille de fonctions printf car il est, par nature, non sécurisé. En présence de %n, le comportement par défaut consiste à appeler le gestionnaire de paramètre non valide. Pour activer la prise en charge de %n, utilisez `_set_printf_count_output` (voir également `_get_printf_count_output`).

- `sprintf` affiche maintenant le signe négatif d’un zéro signé.

- `swprintf` a été modifié pour être conforme à la norme. Il nécessite désormais un paramètre de taille. La forme de `swprintf` sans paramètre de taille a été dépréciée.

- La fonction `_set_security_error_handler` a été supprimée. Supprimez tous les appels à cette fonction ; l’utilisation du gestionnaire par défaut est un moyen beaucoup plus sûr de traiter les erreurs de sécurité.

- `time_t` est maintenant une valeur 64 bits (sauf si _USE_32BIT_TIME_T est défini).

- Les fonctions `_spawn` et `_wspawn` ne modifient plus `errno` en cas de réussite, comme cela est spécifié par la norme C.

- RTC utilise désormais les caractères larges par défaut.

- Les fonctions de prise en charge du mot de contrôle à virgule flottante ont été dépréciées pour les applications compilées avec `/CLR` ou `/CLR:PURE`. Les fonctions concernées sont `_clear87`, `_clearfp`, `_control87`, `_controlfp`, `_fpreset`, `_status87`, `_statusfp`. Vous pouvez désactiver l’avertissement de dépréciation en définissant _CRT_MANAGED_FP_NO_DEPRECATE, mais l’utilisation de ces fonctions dans le code managé est imprévisible et non prise en charge.

- Certaines fonctions retournent maintenant des pointeurs const. L’ancien comportement non const peut être rétabli en définissant _CONST_RETURN. Les fonctions affectées sont

   - memchr, wmemchr

   - strchr, wcschr, _mbschr, _mbschr_l

   - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

   - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

   - strstr, wcsstr, _mbsstr, _mbsstr_l

- Lors de la liaison avec Setargv.obj ou Wsetargv.obj, il n’est plus possible de supprimer le développement d’un caractère générique sur la ligne de commande en l’entourant de guillemets doubles. Pour plus d’informations, consultez [Développement des arguments avec caractères génériques](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Bibliothèque standard (2005)

- La classe d’exception (située dans l’en-tête \<exception>) a été déplacée dans l’espace de noms `std`. Dans les versions précédentes, cette classe était dans l’espace de noms global. Pour résoudre les erreurs indiquant que la classe d’exception est introuvable, ajoutez l’instruction using suivante dans votre code : `using namespace std;`

- Quand `valarray::resize()` est appelé, le contenu de `valarray` est perdu et remplacé par les valeurs par défaut. La méthode `resize()` est destinée à réinitialiser `valarray` plutôt qu’à le développer de façon dynamique comme un vecteur.

- Itérateurs de débogage : les applications générées avec une version debug de la bibliothèque Runtime C et qui utilisent des itérateurs de façon incorrecte peuvent commencer à voir des assertions au moment de l’exécution. Pour désactiver ces assertions, vous devez affecter à _HAS_ITERATOR_DEBUGGING (remplacé par [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) après Visual Studio 2010) la valeur 0. Pour plus d’informations, consultez [Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Modifications avec rupture dans Visual C++ .NET 2003

### <a name="compiler"></a>Compilateur

- Les parenthèses fermantes sont désormais requises pour la directive de préprocesseur définie (C2004).

- Des spécialisations explicites ne trouvent plus de paramètres de modèle dans le modèle principal ([erreur de compilateur C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Un membre protégé (n) est uniquement accessible par l’intermédiaire d’une fonction membre d’une classe (B) qui hérite de la classe (A) dont il (n) est membre ([erreur de compilateur C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Les vérifications de l’accessibilité améliorées dans le compilateur détectent désormais les classes de base inaccessibles ([erreur de compilateur C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Une exception ne peut pas être interceptée si le destructeur et/ou le constructeur de copie est inaccessible (C2316).

- Les arguments par défaut pour les pointeurs vers des fonctions ne sont plus autorisés ([erreur de compilateur C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Les données membres static ne peuvent pas être initialisées par le biais d’une classe dérivée ([erreur de compilateur C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- L’initialisation d’un **typedef** n’est pas autorisée par la norme et génère désormais une erreur ([erreur de compilateur C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- Le type **bool** est maintenant autorisé ([erreur de compilateur C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- Une conversion définie par l’utilisateur (UDC) peut maintenant créer une ambiguïté avec les opérateurs surchargés ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Plus d’expressions sont maintenant considérées comme constantes pointeur null valides ([erreur de compilateur C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- template<> est désormais requis là où le compilateur l’aurait précédemment déduit ([erreur de compilateur C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- La spécialisation explicite d’une fonction membre à l’extérieur de la classe n’est pas valide si la fonction a déjà été spécialisée explicitement par le biais d’une spécialisation de classe de modèle ([erreur de compilateur C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Les paramètres de modèle sans type à virgule flottante ne sont plus autorisés ([erreur de compilateur C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Les modèles de classe ne sont pas autorisés comme arguments de type de modèle (C3206).

- Les noms de fonction friend ne sont plus introduits dans l’espace de noms conteneur ([erreur de compilateur C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Le compilateur n’accepte plus les virgules superflues dans une macro (C4002).

- Un objet de type POD construit avec un initialiseur de la forme () sera initialisé par défaut (C4345).

- typename est désormais requis si un nom dépendant doit être traité comme un type ([avertissement du compilateur (niveau 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Les fonctions incorrectement considérées comme spécialisations de modèle ne le sont plus (C4347).

- Les données membres static ne peuvent pas être initialisées par le biais d’une classe dérivée (C4356).

- Une spécialisation de modèle de classe doit être définie avant d’être utilisée dans un type de retour ([avertissement du compilateur (niveau 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Le compilateur signale désormais un code inaccessible (C4702).

## <a name="see-also"></a>Voir aussi

[Nouveautés de Visual C++ dans Visual Studio](../what-s-new-for-visual-cpp-in-visual-studio.md)
