#include <iostream>
#include <conio.h>
#include <ctime>
#include <list>
#include <queue>
#include <set>
#include <graphics.h>
using namespace std;
// 窗口参数
const int WINDOW_WIDTH = 640;	// 窗口宽度
const int WINDOW_HEIGHT = 480;	// 窗口高度

// 游戏参数
const int MAP_ROWNUM = 20;		// 地图行数
const int MAP_COLNUM = 20;		// 地图列数
const int GRIDGAP = 5;			// 格子间隙
const int GRID = WINDOW_HEIGHT / MAP_COLNUM;	// 大格子宽度
const int _GRID = GRID - 2 * GRIDGAP;			// 小格子宽度
const int SPEED = 50;			// 蛇初始速度
const int ACC = 20;				// 蛇加速度（其实是速度增量）

// 游戏数据结构
enum Direct { RIGHT = 77, DOWN = 80, LEFT = 75, UP = 72 };
struct Coor {
	int x, y, step;
	Coor() { step = 0; }
	Coor(int _x, int _y, int _step = 0) {
		x = _x;
		y = _y;
		step = _step;
	}
	bool operator==(const Coor &t)const {
		return (x == t.x) && (y == t.y);
	}
	bool operator!=(const Coor &t)const {
		return (x != t.x) || (y != t.y);
	}
	bool operator<(const Coor &t)const {
		return x == t.x ? y < t.y : x < t.x;
	}
};

// 各类实现
class Food {
public:
	Coor coor;			// 食物坐标
	bool EXISTFOOD;		// 存在食物
	Food() { EXISTFOOD = true; }
	~Food() { EXISTFOOD = false; }
	// 产生(0,0)~(limx,limy)的坐标
	void RandCoor(int limx, int limy) {
		coor.x = rand() % limx;
		coor.y = rand() % limy;
	}
};

class Snake {
public:
	int length;			// 蛇长度
	int speed;			// 蛇速度
	int acc;			// 加速度
	list<Coor> coor;	// 蛇身坐标
	Direct direct;		// 蛇当前方向
	Snake() {}
	~Snake() {}
	// 蛇移动
	void Move() {
		Coor head = coor.front();
		switch (direct) {
		case UP:	head.y--;	break;
		case DOWN:	head.y++;	break;
		case LEFT:	head.x--;	break;
		case RIGHT:	head.x++;	break;
		}
		coor.pop_back();		// 尾巴出列
		coor.push_front(head);	// 新头入列
	}
	// 蛇转向
	void TurnDirect(char cmd = 0x00) {
		// 使用while而不是if
		if (cmd == 0x00) {
			while (_kbhit()) {
				cmd = _getch();
			}
		}
		// 两次方向相同设置加速度
		if (cmd == direct)
			acc = ACC;
		else
			acc = 0;
		switch (cmd)
		{
		case UP:
			if (direct != DOWN)
				direct = UP;
			break;
		case DOWN:
			if (direct != UP)
				direct = DOWN;
			break;
		case LEFT:
			if (direct != RIGHT)
				direct = LEFT;
			break;
		case RIGHT:
			if (direct != LEFT)
				direct = RIGHT;
			break;
		}
	}
};

class SnakeGame {
private:
	bool isAI;
public:
	Snake snake;
	Food food;
	SnakeGame() { GameInit(); }
	~SnakeGame() {}
	// 游戏初始化
	void GameInit() {
		isAI = false;
		snake.length = 3;
		snake.speed = SPEED;
		snake.acc = 0;
		snake.direct = UP;
		while (!snake.coor.empty()) {
			snake.coor.pop_back();
		}
		Coor body(MAP_ROWNUM / 2, MAP_COLNUM / 2);
		for (int i = 0; i < snake.length; i++) {
			snake.coor.push_back(body);
			body.y++;
		}
		srand((unsigned)time(0));
		food.RandCoor(MAP_COLNUM, MAP_ROWNUM);
	}
	// 画地图
	void DrawMap() {
		setfillcolor(DARKGRAY);
		solidrectangle(0, 0, GRID*MAP_COLNUM, GRID*MAP_ROWNUM);
		setcolor(LIGHTGRAY);
		line(WINDOW_HEIGHT, 0, WINDOW_HEIGHT, WINDOW_HEIGHT);
		// 画食物
		setfillcolor(RED);
		fillrectangle(food.coor.x*GRID + GRIDGAP, food.coor.y*GRID + GRIDGAP,
			(food.coor.x + 1)*GRID - GRIDGAP, (food.coor.y + 1)*GRID - GRIDGAP);
		// 画蛇
		setfillcolor(WHITE);
		Coor temp = snake.coor.front();
		for (auto iter : snake.coor) {
			solidrectangle(iter.x*GRID + GRIDGAP, iter.y*GRID + GRIDGAP,
				(iter.x + 1)*GRID - GRIDGAP, (iter.y + 1)*GRID - GRIDGAP);
			// 画缝隙
			int iter_x = iter.x*GRID + GRIDGAP;
			int iter_y = iter.y*GRID + GRIDGAP;
			int temp_x = temp.x*GRID + GRIDGAP;
			int temp_y = temp.y*GRID + GRIDGAP;
			if (temp.x == iter.x) {
				if (iter.y > temp.y) {
					solidrectangle(temp_x, temp_y + _GRID, iter_x + _GRID, iter_y);
				}
				if (iter.y < temp.y) {
					solidrectangle(iter_x, iter_y + _GRID, temp_x + _GRID, temp_y);
				}
			}
			if (temp.y == iter.y) {
				if (iter.x > temp.x) {
					solidrectangle(temp_x + _GRID, temp_y, iter_x, iter_y + _GRID);
				}
				if (iter.x < temp.x) {
					solidrectangle(iter_x + _GRID, iter_y, temp_x, temp_y + _GRID);
				}
			}
			temp = iter;
		}
	}
	// 处理吃食物
	void EatFood() {
		Coor head = snake.coor.front();
		if (head == food.coor) {
			food.EXISTFOOD = false;
			snake.coor.push_back(snake.coor.back());
			snake.length++;
		}
	}
	// 产生食物
	void CreatFood() {
		if (food.EXISTFOOD == false) {
			list<Coor>::const_iterator iter;
			while (true) {
				food.RandCoor(MAP_COLNUM, MAP_ROWNUM);
				if (!onSnake(food.coor))
					break;
			}
			food.EXISTFOOD = true;
		}
	}
	// 判断游戏结束
	bool GameOver() {
		Coor head = snake.coor.front();
		if (!inBorder(head) || onSnake_ExceptHead(head) || EatFullScreen()) {
			return true;
		}
		return false;
	}
	// 是否吃满食物
	bool EatFullScreen() {
		return snake.length == MAP_COLNUM*MAP_ROWNUM;
	}
	// 游戏结束画面
	void ShowGameEnd() {
		setfillcolor(BLACK);
		/*fillrectangle(0, WINDOW_HEIGHT / 4, WINDOW_HEIGHT, WINDOW_HEIGHT / 4 * 3);*/
		// 在屏幕中央输出字符串
		TCHAR *str_end = _T("GAME OVER!");
		if (EatFullScreen())
			str_end = _T("YOU WIN!");
		// x64会报警告：“size_t”转换到“int”，可能丢失数据
		int Tstrlen = (int)_tcslen(str_end);
		outtextxy(WINDOW_HEIGHT / 2 - Tstrlen * 20 / 4, WINDOW_HEIGHT / 2 - 20 / 4, str_end);
	}
	// 绘制游戏相关信息
	void ShowGameInfo(){
		// 填充黑色底
		setfillcolor(BLACK);
		solidrectangle(WINDOW_HEIGHT, 0, WINDOW_WIDTH, WINDOW_HEIGHT);
		// 尺寸信息
		TCHAR str_mapsize[20];
		swprintf_s(str_mapsize, _T("MAPSIZE:  %d×%d"), MAP_COLNUM, MAP_ROWNUM);
		settextcolor(WHITE);
		outtextxy(WINDOW_HEIGHT + 20, 20, str_mapsize);
		// AI状态信息
		TCHAR *str_ai = _T("AI:  OFF");
		if (isAI == true)	str_ai = _T("AI:  ON");
		outtextxy(WINDOW_HEIGHT + 20, 50, str_ai);
		// 速度信息
		TCHAR str_speed[20];
		swprintf_s(str_speed, _T("SPEED:  %d"), snake.speed + snake.acc);
		outtextxy(WINDOW_HEIGHT + 20, 80, str_speed);
		// 加速度信息
		TCHAR str_acc[20];
		swprintf_s(str_acc, _T("ACC:  %d"), snake.acc);
		outtextxy(WINDOW_HEIGHT + 20, 110, str_acc);
		// 蛇长度信息
		TCHAR str_life[20];
		swprintf_s(str_life, _T("LIFE:  %d/%d"), snake.length, MAP_COLNUM*MAP_ROWNUM);
		outtextxy(WINDOW_HEIGHT + 20, 140, str_life);
		// 保存结点,使用引用是为了处理尾巴设置为可走结点
		const Coor &snakeHead = snake.coor.front();
		const Coor &snakeTail = snake.coor.back();
		// 测试
		TCHAR str_test[20];
		swprintf_s(str_test, _T("找尾巴步数:  %d"), canFindPath(snakeHead, snakeTail));
		outtextxy(WINDOW_HEIGHT + 20, 170, str_test);
		// 食物坐标信息
		TCHAR str_food[20];
		swprintf_s(str_food, _T("食物坐标:  (%d,%d)"), food.coor.x, food.coor.y);
		outtextxy(WINDOW_HEIGHT + 20, 200, str_food);
		// 蛇头坐标信息
		TCHAR str_head[20];
		swprintf_s(str_head, _T("蛇头坐标:  (%d,%d)"), snakeHead.x, snakeHead.y);
		outtextxy(WINDOW_HEIGHT + 20, 230, str_head);
		// 蛇尾坐标信息
		TCHAR str_tail[20];
		swprintf_s(str_tail, _T("蛇尾坐标:  (%d,%d)"), snakeTail.x, snakeTail.y);
		outtextxy(WINDOW_HEIGHT + 20, 260, str_tail);
		// 方向信息
		TCHAR *str_dir;
		switch (snake.direct) {
		case RIGHT:	str_dir = _T("方向:  RIGHT");	break;
		case DOWN:	str_dir = _T("方向:  DOWN");		break;
		case LEFT:	str_dir = _T("方向:  LEFT"); 	break;
		case UP:	str_dir = _T("方向:  UP");		break;
		default:	str_dir = _T("方向:  None");
		}
		outtextxy(WINDOW_HEIGHT + 20, 290, str_dir);
		// 游戏操作说明
		outtextxy(WINDOW_HEIGHT + 20, 320, _T("操作说明:"));
		outtextxy(WINDOW_HEIGHT + 20, 340, _T("使用方向键控制"));
		outtextxy(WINDOW_HEIGHT + 20, 360, _T("长按方向键加速"));
		outtextxy(WINDOW_HEIGHT + 20, 380, _T("上  :      ↑"));
		outtextxy(WINDOW_HEIGHT + 20, 400, _T("下  :      ↓"));
		outtextxy(WINDOW_HEIGHT + 20, 420, _T("左  :      ←"));
		outtextxy(WINDOW_HEIGHT + 20, 440, _T("右  :      →"));
	}

	// AI相关
	void OpenAI() { isAI = true; }
	void CloseAI() { isAI = false; }
	// 得到下一步AI指令--
	char getNextCmd() {
		if (isAI == false)
			return 0x00;
		char cmd = 0x00;
		// 如果能找到食物
		if (canFindFood(snake.coor.front())) {
			// 模拟一条蛇
			SnakeGame simulate = *this;
			// 去吃食物
			while (simulate.food.EXISTFOOD) {
				simulate.snake.TurnDirect(simulate.NextCmdToFood());
				simulate.snake.Move();
				simulate.EatFood();
			}
			// 如果吃完还能找到尾巴/到尾巴的距离大于1
			if (simulate.canFindPath(simulate.snake.coor.front(), simulate.snake.coor.back())>1) {
				// 真正去吃
				cmd = NextCmdToFood();
			}
			else {
				// 吃完找不到
				cmd = NextCmdToFarAway(snake.coor.front());
			}
		}
		else {
			// 找不到食物
			cmd = NextCmdToFarAway(snake.coor.front());
		}
		return cmd;
	}
	// 存在路径返回步数，不存在返回-1
	int canFindPath(const Coor& _start, const Coor& _end) {
		if (_start == _end) {
			return 0;
		}
		const int next[4][2] = { { 1, 0 }, { 0, 1 }, { -1, 0 }, { 0, -1 } }; // 右下左上
		queue<Coor> bfs_que;
		set<Coor> snake_set;
		Coor tcoor;
		bfs_que.push(_start);
		for (auto iter : snake.coor) {
			snake_set.insert(iter);
		}
		// 如果终点是尾巴就把尾巴置为可走结点 *
		// 调用时需要使用引用
		if (&_end == &snake.coor.back()) {
			snake_set.erase(_end);
		}
		while (!bfs_que.empty()) {
			for (int k = 0; k < 4; k++) {
				tcoor.x = bfs_que.front().x + next[k][0];
				tcoor.y = bfs_que.front().y + next[k][1];
				// 超出地图进入下次循环
				if (!inBorder(tcoor)) {
					continue;
				}
				// 无障碍没有走过的结点加入队列
				if (!snake_set.count(tcoor)) {
					tcoor.step = bfs_que.front().step + 1;
					snake_set.insert(tcoor);
					bfs_que.push(tcoor);
				}
				// 到达目标返回步数
				if (tcoor == _end) {
					return tcoor.step;
				}
			}
			bfs_que.pop();
		}
		return -1;
	}
	// 存在到尾巴的路径
	bool canFindTail(Coor _start) {
		return canFindPath(_start, snake.coor.back()) >= 0 ? true : false;
	}
	// 存在到食物的路径
	bool canFindFood(Coor _start) {
		return canFindPath(_start, food.coor) >= 0 ? true : false;
	}
	// 最短距离吃食物
	char NextCmdToFood() {
		const int next[4][2] = { { 1, 0 }, { 0, 1 }, { -1, 0 }, { 0, -1 } }; // 右下左上
		// 得到头部周围4点
		Coor aroundPoint[4];
		for (int i = 0; i < 4; i++) {
			aroundPoint[i].x = snake.coor.front().x + next[i][0];
			aroundPoint[i].y = snake.coor.front().y + next[i][1];
			if (!inBorder(aroundPoint[i]) || onSnake_ExceptTail(aroundPoint[i]))	// 特殊处理尾巴
				aroundPoint[i].step = -1;
			else
				aroundPoint[i].step = canFindPath(aroundPoint[i], food.coor);
		}
		// 选出最近的走
		int minstep_index = 0;
		for (int i = 1; i < 4; i++) {
			// 是0表示是食物直接走
			// 如果是-1不参与比较
			if (aroundPoint[minstep_index].step == -1)
				minstep_index = i;
			if (aroundPoint[i].step != -1) {
				if (aroundPoint[i].step < aroundPoint[minstep_index].step) {
					minstep_index = i;
				}
			}
		}
		char ret = 0x00;
		// 返回操作，找不到食物就返回0x00什么都不做
		if (aroundPoint[minstep_index].step != -1)
			ret = RetCmd(aroundPoint[minstep_index]);
		return ret;
	}
	// 后期吃食物用最远

	// 远离食物--待改进**
	char NextCmdToFarAway(const Coor &coor) {
		const int next[4][2] = { { 1, 0 }, { 0, 1 }, { -1, 0 }, { 0, -1 } }; // 右下左上
		// 得到周围四点曼哈顿距离
		Coor aroundPoint[4];
		for (int i = 0; i < 4; i++) {
			aroundPoint[i].x = snake.coor.front().x + next[i][0];
			aroundPoint[i].y = snake.coor.front().y + next[i][1];
			// 曼哈顿距离,有障碍的点置为-1
			if (canFindTail(aroundPoint[i]) && inBorder(aroundPoint[i]) && !onSnake_ExceptTail(aroundPoint[i]))
				aroundPoint[i].step = getManhattanDistance(aroundPoint[i], coor);
			else // *这里蛇尾应设置为可行
				aroundPoint[i].step = -1;
		}
		// 能到尾巴,远离食物
		// 另一种策略是选离尾巴远的
		int maxstep_index = 0;
		for (int i = 1; i < 4; i++) {
			// 等于号很重要
			if ((aroundPoint[i].step >= aroundPoint[maxstep_index].step)) {
				maxstep_index = i;
			}
		}
		char cmd = 0x00;
		if (aroundPoint[maxstep_index].step != -1)
			cmd = RetCmd(aroundPoint[maxstep_index]);
		return cmd;
	}
	// 最远距离追尾巴
	char NextCmdToTail() {
		const int next[4][2] = { { 1, 0 }, { 0, 1 }, { -1, 0 }, { 0, -1 } }; // 右下左上
		// 得到头部周围4点
		Coor aroundPoint[4];
		for (int i = 0; i < 4; i++) {
			aroundPoint[i].x = snake.coor.front().x + next[i][0];
			aroundPoint[i].y = snake.coor.front().y + next[i][1];
			if (inBorder(aroundPoint[i]) && !onSnake_ExceptTail(aroundPoint[i]))	//	*特殊处理尾巴
				aroundPoint[i].step = canFindPath(aroundPoint[i], snake.coor.back());
			else
				aroundPoint[i].step = -1;
		}
		// 选出最远的点
		int maxstep_index = 0;
		for (int i = 1; i < 4; i++) {
			// 是0表示是食物直接走
			// 如果是-1不参与比较
			if (aroundPoint[maxstep_index].step == -1)
				maxstep_index = i;
			if (aroundPoint[i].step != -1) {
				if (aroundPoint[i].step > aroundPoint[maxstep_index].step) {
					maxstep_index = i;
				}
			}
		}
		char ret = 0x00;
		// 返回操作，找不到食物就返回0x00什么都不做
		if (aroundPoint[maxstep_index].step != -1)
			ret = RetCmd(aroundPoint[maxstep_index]);
		return ret;
	}
	// 返回可用的指令,必须是周围4点
	char RetCmd(Coor nextPoint) {
		char cmd = 0x00;
		int dx = nextPoint.x - snake.coor.front().x;
		int dy = nextPoint.y - snake.coor.front().y;
		if (dx == 0 && dy < 0)
			cmd = UP;
		if (dx == 0 && dy > 0)
			cmd = DOWN;
		if (dx < 0 && dy == 0)
			cmd = LEFT;
		if (dx > 0 && dy == 0)
			cmd = RIGHT;
		return cmd;
	}
	// 两点曼哈顿距离
	int getManhattanDistance(Coor _a, Coor _b) {
		return abs(_a.x - _b.x) + abs(_a.y - _b.y);
	}
	// 坐标在蛇上/包括蛇头蛇尾
	bool onSnake(Coor coor) {
		for (auto iter : snake.coor) {
			if (coor == iter) {
				return true;
			}
		}
		return false;
	}
	// 坐标在蛇上/不包括蛇头
	bool onSnake_ExceptHead(Coor coor){
		auto iter = snake.coor.begin();
		for (iter++; iter != snake.coor.end(); iter++) {
			if (coor == *iter) {
				return true;
			}
		}
		return false;
	}
	// 坐标在蛇上/不包括蛇尾
	bool onSnake_ExceptTail(Coor coor) {
		auto iter = snake.coor.begin();
		auto flag = --snake.coor.end();
		for (; iter != flag; iter++) {
			if (coor == *iter) {
				return true;
			}
		}
		return false;
	}
	// 坐标在方框里
	bool inBorder(Coor coor)const {
		return (coor.x >= 0 && coor.x < MAP_COLNUM && coor.y >= 0 && coor.y < MAP_ROWNUM);
	}
};

// 程序入口
int main() {
	// 加参数, SHOWCONSOLE开启控制台
	initgraph(WINDOW_WIDTH, WINDOW_HEIGHT);
	// 开启双缓冲绘图
	BeginBatchDraw();
	SnakeGame SG;
	SG.OpenAI();
	_getch();
	while (true) {
		SG.EatFood();
		SG.CreatFood();
		SG.snake.TurnDirect(SG.getNextCmd());
		SG.snake.Move();
		if (SG.GameOver()) {
			SG.DrawMap();
			SG.ShowGameEnd();
			SG.ShowGameInfo();	//显示最终信息
			FlushBatchDraw();
			_getch();
			SG.GameInit();
			SG.OpenAI();
		}
		SG.ShowGameInfo();
		SG.DrawMap();
		FlushBatchDraw();
		Sleep(1000 / (SG.snake.speed + SG.snake.acc));
	}
	EndBatchDraw();
	closegraph();
	return 0;
}
