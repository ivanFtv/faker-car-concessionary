AFL-1.1

Copyright (c) 2022 Ivan Pellegatta

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


To install in Laravel:
```
composer require ivanpellegatta84/faker-car-concessionary
```

Use example in Laravel Factories:
````
<?php

namespace Database\Factories;
use Illuminate\Database\Eloquent\Factories\Factory;


class CarFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition()
    {
        $fakercar = (new \Faker\Factory())::create();
        $fakercar->addProvider(new \Faker\Provider\Fakecar($fakercar));
       
        return [
            'manufacturers_id' => $fakercar->numberBetween($min = 0, $max = 50),
            'model' => $fakercar->vehicleModel(),
            'year' => $fakercar->biasedNumberBetween(1998,2017, 'sqrt'),
            'engine' => $fakercar->vehicleEnginePower(),
            'price' => $fakercar->biasedNumberBetween(10000,120000, 'sqrt'),
            'discount' => $fakercar->numberBetween($min = 0, $max = 20),
            'transmission' => $fakercar->vehicleGearBoxType(),
            'power' => $fakercar->vehicleFuelType(),
            'color' => $fakercar->colorName(),
            'door' => $fakercar->vehicleDoorCount(),
            'properties' => implode(', ', $fakercar->vehicleProperties())
        ];
    }
}
````

Method inside Faker Car Concessionary:

````
vehicleType();
vehicleFuelType():
vehicleRegistration();
vehicleEnginePower();
vehicleDoorCount();
vehicleSeatCount();
vehicleProperties();
vehicleGearBoxType();
vehiclePaymentMethod();
````

