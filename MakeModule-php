<?php

namespace App\Console\Commands;

use Illuminate\Console\Command;
use Illuminate\Support\Facades\File;

class MakeModule extends Command
{
    protected $signature = 'make:module {name : The name of the module}';
    protected $description = 'Crea la estructura completa de carpetas y clases base para un nuevo módulo en app/src';

    public function handle()
    {
        $module = ucfirst($this->argument('name'));
        $basePath = app_path("src/{$module}");

        $structure = [
            'Http/Controllers' => "{$module}Controller.php",
            'Http/Requests'    => "{$module}Request.php",
            'Models'           => "{$module}.php",
            'Services'         => "{$module}Service.php",
            'DTOs'             => "{$module}DTO.php",
            'Console'          => "{$module}Command.php",
            'Repositories'     => "{$module}Repository.php",
            'Routes'           => "web.php",
        ];

        foreach ($structure as $folder => $fileName) {
            $dirPath = "{$basePath}/{$folder}";
            File::makeDirectory($dirPath, 0755, true, true);

            $filePath = "{$dirPath}/{$fileName}";

            if (!File::exists($filePath)) {
                $namespace = "App\\src\\{$module}\\" . str_replace('/', '\\', $folder);
                $className = pathinfo($fileName, PATHINFO_FILENAME);
                $content = "<?php\n\nnamespace {$namespace};\n\n";

                switch ($folder) {
                    case 'Http/Controllers':
                        $content .= "use App\\Http\\Controllers\\Controller;\n\nclass {$className} extends Controller\n{\n    // TODO: Implement controller methods\n}\n";
                        break;

                    case 'Http/Requests':
                        $content .= "use Illuminate\\Foundation\\Http\\FormRequest;\n\nclass {$className} extends FormRequest\n{\n    public function rules(): array\n    {\n        return [\n            //\n        ];\n    }\n}\n";
                        break;

                    case 'Models':
                        $content .= "use Illuminate\\Database\\Eloquent\\Model;\n\nclass {$className} extends Model\n{\n    protected \$guarded = [];\n}\n";
                        break;

                    case 'Console':
                        $content .= "use Illuminate\\Console\\Command;\n\nclass {$className} extends Command\n{\n    protected \$signature = 'command:name';\n    protected \$description = 'Command description';\n\n    public function handle()\n    {\n        //\n    }\n}\n";
                        break;

                    case 'Routes':
                        $content = "<?php\n\nuse Illuminate\\Support\\Facades\\Route;\n\nRoute::prefix('" . strtolower($module) . "')\n    ->middleware('web')\n    ->group(function () {\n        // Rutas para el módulo {$module}\n    });\n";
                        break;

                    default:
                        $content .= "class {$className}\n{\n    // TODO: Implement\n}\n";
                        break;
                }

                File::put($filePath, $content);
                $this->info("Archivo creado: {$filePath}");
            } else {
                $this->warn("Ya existe: {$filePath}");
            }
        }

        return Command::SUCCESS;
    }
}
