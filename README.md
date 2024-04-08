# -Функция для чтения данных из файла и подсчета количества записей:

const fs = require('fs');
const path = require('path');

const countRecords = (filePath) => {
  const data = fs.readFileSync(path.resolve(__dirname, filePath), 'utf-8').split('\n').slice(1);
  return data.length;
};

const filePath = process.argv[2];
const count = countRecords(filePath);
console.log(`Количество автомобилей: ${count}`);


Функция для вычисления среднего пробега всех автомобилей:

const fs = require('fs');
const path = require('path');

const calculateAverageMileage = (filePath) => {
  const data = fs.readFileSync(path.resolve(__dirname, filePath), 'utf-8').split('\n').slice(1);

  const totalMileage = data.reduce((acc, curr) => {
    const [, , , , mileage] = curr.split(',');
    return acc + parseInt(mileage, 10);
  }, 0);

  const averageMileage = Math.round(totalMileage / data.length);
  return averageMileage;
};

const filePath = process.argv[2];
const averageMileage = calculateAverageMileage(filePath);
console.log(`Средний пробег: ${averageMileage}`);


Функция для определения стоимости самой дорогой машины:

const fs = require('fs');
const path = require('path');

const findMaxPrice = (filePath) => {
  const data = fs.readFileSync(path.resolve(__dirname, filePath), 'utf-8').split('\n').slice(1);

  let maxPrice = 0;
  data.forEach((record) => {
    const [, , , , , , , price] = record.split(',');
    const currentPrice = parseInt(price, 10);
    if (currentPrice > maxPrice) {
      maxPrice = currentPrice;
    }
  });

  return maxPrice;
};

const filePath = process.argv[2];
const maxPrice = findMaxPrice(filePath);
console.log(`Стоимость самой дорогой машины: ${maxPrice}`);
