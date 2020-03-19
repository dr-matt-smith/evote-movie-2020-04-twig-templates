# evote-movie-2020-04-twig-templates

- add Twig with

    `composer req twig/twig`

- update `MainController` to create a private `Twig` instance variable `$twig` when created

    ```php
    class MainController
    {
        const PATH_TO_TEMPLATES = __DIR__ . '/../templates';
        private $twig;
    
        public function __construct()
        {
            $this->twig = new \Twig\Environment(new \Twig\Loader\FilesystemLoader(self::PATH_TO_TEMPLATES));
        }
    ```

- rename each file in `/templates` in the form `<PAGE>.html.twig`

- update each `MainController` method to use `$twig` object to create and print HTML for each template, e.g.

    ```php
    public function home()
    {
        $template = 'index.html.twig';
        $args = [];
        $html = $this->twig->render($template, $args);
        print $html;
    }
    ```