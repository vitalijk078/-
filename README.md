1. Выведите средний пробег всех автомобилей
  const totalMileage = data.reduce((acc, curr) => {
    const mileage = parseInt(curr.split(',')[4], 10);
    return acc + mileage;
  }, 0);
  const averageMileage = Math.round(totalMileage / (data.length - 1));
  console.log(`Средний пробег: ${averageMileage}`);
